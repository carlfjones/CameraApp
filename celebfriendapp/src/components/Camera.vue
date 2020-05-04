<template>
    <div class="camera">
        <video autoplay class="feed"></video>
        <button class="snap">Snap</button>
    </div>
</template>

<script>
export default {
    name: "camera"
}
</script>

<style lang="scss" scoped>
.camera {
    width: 100vw;
    height: 100vh;

    .feed {
        width:100%;
        max-width: 1280px;
        box-shadow: 4px 4px 12px 0px rgba(0, 0, 0, 0.25);
    }
}
</style>