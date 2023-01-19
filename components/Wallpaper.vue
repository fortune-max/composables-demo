<script setup>
    import { useNow } from '@vueuse/core'

    const now = useNow();
    const currTime = computed(() => `${now.value.getHours().toString().padStart(2, '0')}:${now.value.getMinutes().toString().padStart(2, '0')}:${now.value.getSeconds().toString().padStart(2, '0')}`);
    const currDay = computed (() => now.value.toDateString().slice(0, -5));
</script>

<template>
    <div id="wallpaper-container">
        <img id="wallpaper-img" src="/wallpaper.jpg" />
        <span id="time-disp">{{ currTime }}</span>
        <span id="date-disp">{{ currDay }}</span>
    </div>
</template>

<style scoped>
    #wallpaper-img {
        height: 696px;
        width: 313.2px;
        border-radius: 10px;
    }

    #time-disp {
        color: white;
        font-size: 47px;
        position: relative;
        right: 240px;
        bottom: 546px;
    }

    #date-disp {
        color: white;
        font-size: 20px;
        position: relative;
        right: 366px;
        bottom: 516px;
    }

    #wallpaper-container {
        display: inline-block;

        /* style for placing in phone frame */
        position: relative;
        right: 504px;
        bottom: 13px;
    }
</style>