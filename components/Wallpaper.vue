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
        color: black;
        font-size: 47px;
        position: relative;
        right: 250px;
        bottom: 546px;
        font-family: "PT Sans";
    }

    #date-disp {
        color: black;
        font-size: 20px;
        position: relative;
        right: 376px;
        bottom: 516px;
        font-family: "PT Sans";
    }

    #wallpaper-container {
        display: inline-block;

        /* style for placing in phone frame */
        position: relative;
        right: 329px;
        bottom: 13px;
    }
</style>
