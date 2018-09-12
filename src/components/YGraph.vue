<template>
    <div class="vertical-chart">
      <span>N points: {{this.points.length}}</span>
      <Bar v-for="bar in this.binPoints(this.points, this.yHist, 'y')" :key="bar.id" :new_bar="bar" :maxLength="Math.max(...bars.allLengths)"/>
    </div>
</template>

<script>
  import Bar from './Bar.vue'
  export default {
    components: { Bar },
    props: ['points', 'colors', 'yHist'],
    data () {
      return {
      }
    },
    methods: {
      binPoints: function (points, hist, axis) {
        hist.bars.map(bar => {
          // filter points based on bin
          var binPoints = points.filter(point => point[axis] >= bar.range[0] && point[axis] < bar.range[1])

          // map and count per color
          var barColors = Array(...bar.colors)
          binPoints.map(function (point) {
            if (!barColors[point.color]) {
              barColors[point.color] = 0
            }
            barColors[point.color]++
          })
          console.log(bar, barColors)
        })

        //   binnedPoints.push({id: `${binStart}-${binStop}-${binPoints.length}`, range: [binStart, binStop], colors: colors, size: binPoints.length})
        //   allLengths.push(binPoints.length)
        // }
        // return {bars: binnedPoints, allLengths: allLengths}
      }
    }
  }
</script>

<style>
  .vertical-chart {
    width: 100%;
    display: grid;
  }
</style>
