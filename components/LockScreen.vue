<script setup>
    const props = defineProps(["currTime", "currDay"]);
</script>

<template>
    <div id="lockscreen-container">
        <img id="lockscreen-img" src="/lockscreen.jpg" />
        <span id="time-disp">{{ props.currTime }}</span>
        <span id="date-disp">{{ props.currDay }}</span>
    </div>
</template>

<style scoped>
    #lockscreen-img {
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

    #lockscreen-container {
        display: inline-block;

        /* style for placing in phone frame */
        position: relative;
        right: 329px;
        bottom: 13px;
    }
</style>
