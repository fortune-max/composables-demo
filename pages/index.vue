<script setup>
import { useBattery } from '@vueuse/core'
import { promiseTimeout } from '@vueuse/core'
import { whenever } from '@vueuse/core'
import { useNow } from '@vueuse/core'

// Battery stuff
const { charging, level } = useBattery();
const batteryLevel = computed(() => level.value * 100);
const showCharging = ref(false);

whenever(charging, async () => {
    showCharging.value = true;
    await promiseTimeout(2000);
    showCharging.value = false;
});

// Time stuff
const now = useNow();
const currTime = computed(() => `${now.value.getHours().toString().padStart(2, '0')}:${now.value.getMinutes().toString().padStart(2, '0')}:${now.value.getSeconds().toString().padStart(2, '0')}`);
const currDay = computed (() => now.value.toDateString().slice(0, -5));

</script>

<template>
    <PhoneFrame/>
    <ChargingScreen :battery-level="batteryLevel" v-show="showCharging"/>
    <LockScreen :curr-time="currTime" :curr-day="currDay"/>
    
</template>
