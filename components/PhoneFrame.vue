<template>
    <div id="phone_frame">
        <img id="pixel_img" src="/pixel_frame.png" />
    </div>
</template>

<style scoped>
    #pixel_img {
        height: 720px;
    }

    #phone_frame {
        margin-left: 50%;
        margin-top: 20px;
        margin-bottom: 20px;
        display: inline-block;
        transform: translateX(-50%);
    }
</style>