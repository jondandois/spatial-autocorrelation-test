<template>
  <section class="full-width">
    <button v-on:click="drawRandomPoint">Random Point</button>
    <button>100 Random Points</button>
    <button>Random Cluster</button>
  </section>
</template>

<script>
  export default {
    props: ['points', 'colors'],
    data () {
      return {}
    },
    methods: {
      drawRandomPoint: function () {
        var point = this.randomPoint()
        var color = this.getColor()
        var size = this.d3()
        var newPoint = [point.x, 5, color, size]
        console.log(newPoint)
        this.points.splice(this.points.length + 1, 1, newPoint)
      },

      getColor: function () {
        return this.colors[this.d6() - 1]
      },

      randomPoint: function () {
        var x = this.getRandomArbitrary(0, 600)
        var y = this.getRandomArbitrary(0, 300)
        return {x: x, y: y}
      },

      getRandomArbitrary: function (min, max) {
        return Math.floor(Math.random() * (max - min) + min)
      },

      // dice functions
      dN: function (n) {
        return this.getRandomArbitrary(1, n + 1)
      },

      d6: function () { return this.dN(6) },
      d3: function () { return this.dN(3) }
    }
  }
</script>

<style>

</style>
