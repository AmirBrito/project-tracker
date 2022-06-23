<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <StopWatch :timeInSeconds="timeInSeconds" />
    <ButtonTracker
      @clicked="startCount"
      iconButton="play"
      textButton="Play"
      :disabled="runningWatch"
    />
    <ButtonTracker
      @clicked="finishCount"
      iconButton="stop"
      textButton="Stop"
      :disabled="!runningWatch"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopWatch from "./StopWatch.vue";
import ButtonTracker from "./ButtonTracker.vue";

export default defineComponent({
  name: "TimerTracker",
  emits: ["timerTrackerFinished"],
  components: {
    StopWatch,
    ButtonTracker,
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
