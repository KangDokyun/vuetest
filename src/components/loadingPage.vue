<template>
<div id="loadingPage">
  <img :src="loadingImg">
</div>
</template>

<script>
export default {
  name: 'loadingPage',
  data () {
    return {
      loadingImg: './static/transparent_loading3.gif'
    }
  },
  mounted: function () {
    setTimeout(() => {
      this.$emit('loaded')
    }, 2000)
  }
}
</script>

<style scoped>
#loadingPage {
  display: flex;
  width: 100%;
  flex-flow: column nowrap;
  justify-content: center;
  align-items: center;
}
img {
  background: transparent;
  width: 40%;
}
</style>