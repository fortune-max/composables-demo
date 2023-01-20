<script setup>
    const props = defineProps(["batteryLevel"]);
    const batteryLevel = computed(() => Math.max(Math.min(props.batteryLevel, 99), 10));
</script>

<template>
    <div id="charging_screen_container">
        <img id="charging_img" src="/charging.jpg" />
        <span id="charge_lvl">{{ batteryLevel }}</span>
    </div>
</template>

<style scoped>
    #charging_screen_container {
        display: inline-block;

        /* style for placing in phone frame */
        position: relative;
        right: 329px;
        bottom: 16px;
    }

    #charging_img {
        height: 696px;
        border-radius: 10px;
    }

    #charge_lvl {
        color: white;
        font-size: 36px;
        position: relative;
        right: 176px;
        bottom: 346px;
    }
</style>