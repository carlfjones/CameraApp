<template>
    <div class="camera">
        <video autoplay class="feed"></video>
        <button class="snap">SNAP</button>
    </div>
</template>

<script>
export default {
    name: "camera",
    methods: {
        init() {
            if ('mediaDevices' in navigator && 'getUserMedia' in navigator.mediaDevices) {
                navigator.mediaDevices.getUserMedia({video:true}).then(stream => {
                   const videoPlayer = document.querySelector("video");
                   videoPlayer.srcObject = stream;
                   videoPlayer.play();
                });
            } else {
                alert("Cannot get Media Devices");
            }
        }
    },
    beforeMount() {
        this.init();
    }
}
</script>

<style lang="scss" scoped>
.camera {
    width: 100vw;
    height: 100vh;
    padding: 25px;

    .feed {
        box-sizing: border-box;
        background-color: #161616;
        display: block;
        margin: 0 auto;
        width:100%;
        max-width: 1280px;
        box-shadow: 6px 6px 12px 0px rgba(0, 0, 0, 0.35);
    }

    .snap {
        margin: 25px auto;
        display: block;
        color: #08718b;
        width: 75px;
        height: 75px;
        border-radius: 50%;
        background-color: transparentize($color: #7a7a7a, $amount: 0.75);
        border: 1px solid #171717;
        outline: none;
        cursor: pointer;

        &:hover {
            background-color: transparentize($color: #177f86, $amount: 0.2);
        }
        &:active {
            background-color: darken($color: #177f86, $amount: 0.5);
        }
    }
}
</style>