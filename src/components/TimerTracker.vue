<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <StopWatch :timeInSeconds="timeInSeconds" />
    <button class="button" @click="startCount">
      <span class="icon">
        <fa icon="play" />
      </span>
      <span>Play</span>
    </button>
    <button class="button" @click="finishCount">
      <span class="icon">
        <fa icon="stop" />
      </span>
      <span>Stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopWatch from "./StopWatch.vue";

export default defineComponent({
  name: "TimerTracker",
  components: {
    StopWatch,
  },
  data() {
    return {
      timeInSeconds: 0,
      stopWatch: 0,
    };
  },
  methods: {
    startCount() {
      this.stopWatch = setInterval(() => {
        this.timeInSeconds++;
      }, 1000);
    },
    finishCount() {
      clearInterval(this.stopWatch);
    },
  },
});
</script>
