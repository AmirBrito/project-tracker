<template>
  <section>
    <strong class="stop-watch-display">{{ timeElapsed }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "StopWatch",
  props: {
    timeInSeconds: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    timeElapsed(): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style scoped>
.stop-watch-display {
  color: var(--primary-text);
}
</style>
