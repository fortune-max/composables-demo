<script setup>
    const props = defineProps(["currTime", "currDay", "opacity", "batteryLevel"]);
</script>

<template>
    <div id="homescreen-container" :style="{opacity: props.opacity}">
        <img id="homescreen-img" src="/homescreen.jpg" />
        <span id="time-disp">{{ props.currTime.slice(0,5) }}</span>
        <span id="date-disp">{{ props.currDay }}</span>
        <span id="battery-disp">{{ props.batteryLevel }}%</span>
    </div>
</template>

<style scoped>
    #homescreen-img {
        height: 696px;
        width: 313.2px;
        border-radius: 10px;
    }

    #homescreen-container {
        display: inline-block;

        /* style for placing in phone frame */
        position: relative;
        right: 329px;
        bottom: 13px;
    }

    #time-disp {
        color: white;
        font-size: 47px;
        position: relative;
        right: 290px;
        bottom: 596px;
        font-family: "PT Sans";
    }

    #date-disp {
        color: white;
        font-size: 15px;
        position: relative;
        right: 396px;
        bottom: 576px;
        font-family: "PT Sans";
    }

    #battery-disp {
        color: white;
        font-size: 11px;
        position: relative;
        right: 199px;
        bottom: 676px;
        font-family: "PT Sans";
    }
</style>