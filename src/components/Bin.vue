<template>
  <div class="bin" v-bind:style="styleObject"></div>
</template>

<script>
  export default {
    props: ['color', 'size', 'count'],
    data () {
      return {
        styleObject: {
          background: this.color,
          width: this.size + '%'
        }
      }
    }
  }
</script>

<style>
  .bin  {
    float: left;
    height: 100%;
    opacity: 0.75;
  }
</style>
