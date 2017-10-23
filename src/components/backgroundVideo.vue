<template>
  <video autoplay muted loop :src='videoSrc'></video>
</template>

<script>
export default {
  name: 'backgroundVideo',
  data () {
    return {
      videoSrc: 'https://video.wixstatic.com/video/11062b_40811fcc9cac4a5bbfb0d93aaa94d70d/1080p/mp4/file.mp4'
    }
  }
}
</script>

<style scoped>
video{
  position: fixed;
  right: 0;
  bottom: 0;
  min-width: 100%;
  min-height: 100%;
  width: auto;
  height: auto;
  z-index: -9999;
}
</style>


