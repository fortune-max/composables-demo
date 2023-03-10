<script setup>
import { format } from 'date-fns'
import { useBattery } from '@vueuse/core'
import { promiseTimeout } from '@vueuse/core'
import { whenever } from '@vueuse/core'
import { useNow } from '@vueuse/core'
import { useIdle } from '@vueuse/core'
import { TransitionPresets, useTransition } from '@vueuse/core'
import { onKeyStroke } from '@vueuse/core'

// Battery stuff
const { charging, level } = useBattery();
const batteryLevel = computed(() => Math.round(level.value * 100));
const showCharging = ref(false);

whenever(charging, async () => {
    showCharging.value = true;
    await promiseTimeout(2000);
    showCharging.value = false;
});

// Time stuff
const now = useNow();
const currTime = computed(() => format(now.value, 'HH:mm:ss'));
const currDay = computed(() => format(now.value, 'EEE MMM d'));

// Screen unlock on keypress
const screenIsLocked = ref(true);
onKeyStroke(true, (e) => {
    screenIsLocked.value = false;
});

// Idle stuff
const showLockScreen = ref(true);
const { idle } = useIdle(5 * 1000); // milliseconds
const notIdle = computed(() => !idle.value);

whenever(idle, () => {
    showLockScreen.value = false;
    screenIsLocked.value = true;
});

whenever(notIdle, () => {
    showLockScreen.value = true;
});

// Transition stuff
const idleNum = computed(() => +!idle.value);
const brightness = useTransition(idleNum, {
  duration: 1000,
  transition: TransitionPresets.easeInOutCubic,
});

</script>

<template>
    <PhoneFrame/>
    <ChargingScreen :battery-level="batteryLevel" v-show="showCharging"/>
    <LockScreen :curr-time="currTime" :curr-day="currDay" :opacity="brightness" v-show="screenIsLocked && !showCharging"/>
    <HomeScreen :curr-time="currTime" :curr-day="currDay" :battery-level="batteryLevel" :opacity="brightness" v-show="!screenIsLocked && !showCharging"/>
</template>
