<template>
  <div id='app' class='wrapper'>
    <ButtonHeader :points="points" :colors="colors" />
    <MapCanvas :points="points" />
    <YGraph :points="points" :colors="colors" :yHist="yHist"/>
    <section>Data</section>
    <InfoFooter />
  </div>
</template>

<script>
  import InfoFooter from './components/InfoFooter.vue'
  import ButtonHeader from './components/ButtonHeader.vue'
  import MapCanvas from './components/MapCanvas.vue'
  import YGraph from './components/YGraph.vue'
  import samplePoints from './assets/sample_points.js'

  export default {
    components: { InfoFooter, ButtonHeader, MapCanvas, YGraph },
    name: 'app',
    data () {
      return {
        points: samplePoints.points,
        colors: this.colorDefs(),
        yHist: this.initBars('y')
      }
    },
    methods: {
      colorDefs: function () {
        return ['red', 'orange', 'yellow', 'green', 'blue', 'purple']
      },
      initBars: function (axis) {
        var binnedPoints = []
        const range = [0, 300]
        const binWidth = 10
        var nBins = range[1] / binWidth
        for (var i = 0; i < nBins; i++) {
          var colors = {}
          this.colorDefs().forEach(function (color) { colors[color] = 0 })
          var binStart = i * binWidth
          var binStop = (i + 1) * binWidth
          binnedPoints.push({id: `${binStart}-${binStop}`, range: [binStart, binStop], colors: colors, size: 0})
        }
        return {
          allLengths: [],
          bars: binnedPoints
        }
      }
    }
  }
</script>

<style>
  body {
    font-family: 'Dosis', Helvetica, sans-serif;
  }

  .wrapper {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    grid-template-rows: 2em 20em 2em;
  }

  .full-width {
    grid-column-start: 1;
    grid-column-end: 4;
  }

  .wrapper > * {
    border: 1px solid gray;
    border-radius: 2px;
  }

</style>
