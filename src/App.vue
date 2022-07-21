<template>
  <div id="app">
    <input type="range" min="0" max="100" step="1" v-model="progress1">
    <input type="range" min="0" max="360" step="1" v-model="hsl">

    <h2>HTML Skills ({{progress1}})</h2>
    <ProgressBar
        :progressValue="progress1"
        :color="currentColor"
    ></ProgressBar>

    <h2>CSS Skills ({{progress2}})</h2>
    <ProgressBar :progressValue="progress2" color="blue"></ProgressBar>


    <h2>JS Skills ({{progress3}})</h2>
    <button @click="increment">Increment</button>
    <ProgressBar :progressValue="progress3"></ProgressBar>
  </div>
</template>

<script>

import ProgressBar from "./components/ProgressBar";
export default {
  components: {ProgressBar},
  data() {
    return {
      // currentColor: '#ff0000',
      progress1: 0.43,
      max1: 1,
      progress3: 0,
      visible: true,
      hsl: 0,
    }
  },

  methods: {
    increment() {
      this.progress3 += 10;

      if (this.progress3 > 100) {
        this.progress3 = 0;
      }
    }
  },

  computed: {
    currentColor() {
      return `hsl(${this.hsl}, 100%, 50%)`;
    },
    progress2() {
      return Math.max(100 - this.progress1, 0);
    }
  },

  mounted() {

  }
}
</script>

<style>

</style>
