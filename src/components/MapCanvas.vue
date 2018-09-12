<template>
  <canvas id="canvas"></canvas>
</template>

<script>
  export default {
    props: ['points'],
    ready: function () {
      console.log(this.points)
      this.drawPoints(this.points)
    },
    methods: {
      drawPoints: function (points) {
        console.log(points)
      }
    }
  }
</script>

<style>
  #canvas {
    width: 99%;
    height: 99%;
  }
</style>
