<template>
  <div id="app">
    <div class="headers">
          <h2>Celeb Pic App</h2>
        <h4>Click the Snap button and scroll down to see your pic!</h4>
    </div>

    <Camera v-on:takePicture= "this.takePicture" />
    <Gallery />
  </div>
</template>

<script>
import Camera from './components/Camera';
import Gallery from './components/Gallery';

export default {
  name: 'App',
  components: {
    Camera,
    Gallery,
  },
  methods: {
    takePicture () {
      let ratio = (window.innerHeight < window.innerWidth) ? 16 / 9 : 9 / 16;
      const picture = document.querySelector("canvas");
      picture.width = (window.innerWidth < 1280) ? window.innerWidth : 1280;
      picture.height = window.innerWidth / ratio;
      const ctx = picture.getContext("2d");
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality = "high";
      ctx.drawImage(document.querySelector("video"), 0, 0, picture.width, picture.height);
    }
  }
}
</script>

<style lang="scss">
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #F3F3F3;
}
.headers {
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
