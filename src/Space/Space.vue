<template>
  <canvas ref="canvas"></canvas> 
</template>

<script>
  import init from './init'

  export default {
    mounted() {
      init(this.$refs.canvas)
    }
  }
</script>


<style scoped lang="scss">
  $dark-blue: rgb(11, 21, 56);

  canvas{
    background-color: $dark-blue;
    display: block;
  }
</style>

