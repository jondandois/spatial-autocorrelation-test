<template>
  <div class="horizontal-bar">
    <Bin v-for="(size, color) in bar.colors" :key="'Date.now()' + '-' + color + '-bin'" :color="color" :size="100*(size/maxLength)" :count="bar.size"/>
    <span class="bar-label">{{bar.size}}</span>
  </div>
</template>

<script>
  import Bin from './Bin.vue'
  export default {
    components: { Bin },
    props: ['new_bar', 'maxLength'],
    data () {
      return {
        bar: this.parseBar(this.new_bar)
      }
    },
    methods: {
      parseBar: function (bar) {
        return bar
      }
    }
  }
</script>

<style>
  .horizontal-bar {
    height: 10px;
    width: 95%;
    font-size: 0.85em;
  }
</style>
