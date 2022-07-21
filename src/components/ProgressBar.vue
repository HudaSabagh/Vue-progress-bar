<template>
  <div class="progress-bar">
    <div class="bar" :style="barStyles">
      <span>
        {{ progressValueAsPercent }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'progressValue',
    'color',
    'max'
  ],
  computed: {
    progressValueAsPercent() {
      let safeMax = this.max;

      if (safeMax == null || safeMax < 0) {
        safeMax = 100;
      }

      let value = Math.max(this.progressValue, 0);

      const percent = Math.min(
          Math.round(((1 / safeMax) * value) * 100),
          100
      );
      return percent + '%';
    },
    barStyles() {
      return {
        width: this.progressValueAsPercent,
        backgroundColor: this.color,
      }
    }
  }
}
</script>

<style scoped>
.progress-bar {
  border-radius: 9999px;
  background-color: #ccc;
  overflow: hidden;
}

.bar {
  transition: width 0.5s ease-out;
  width: 76%;
  background-color: aqua;
  text-align: right;
}

span {
  padding-right: 0.5em;
  padding-left: 0.5em;
  font-size: 0.8em;
}
</style>
