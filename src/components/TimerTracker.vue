<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <StopWatch :timeInSeconds="timeInSeconds" />
    <button class="button" @click="startCount" :disabled="runningWatch">
      <span class="icon">
        <fa icon="play" />
      </span>
      <span>Play</span>
    </button>
    <button class="button" @click="finishCount" :disabled="!runningWatch">
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
  emits: ["timerTrackerFinished"],
  components: {
    StopWatch,
  },
  data() {
    return {
      timeInSeconds: 0,
      stopWatch: 0,
      runningWatch: false,
    };
  },
  methods: {
    startCount() {
      this.runningWatch = true;
      this.stopWatch = setInterval(() => {
        this.timeInSeconds++;
      }, 1000);
    },
    finishCount() {
      this.runningWatch = false;
      clearInterval(this.stopWatch);
      this.$emit("timerTrackerFinished", this.timeInSeconds);
      this.timeInSeconds = 0;
    },
  },
});
</script>
