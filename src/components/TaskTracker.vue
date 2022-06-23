<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">{{ task.description }}</div>
      <div class="column">
        <StopWatch :time-in-seconds="task.durationInSeconds" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import ITaskTracker from "../interfaces/ITaskTracker";
import { defineComponent, PropType } from "vue";
import StopWatch from "./StopWatch.vue";

export default defineComponent({
  name: "TaskTracker",
  components: {
    StopWatch,
  },
  props: {
    task: {
      type: Object as PropType<ITaskTracker>,
      required: true,
    },
  },
});
</script>

<style scoped>
.box {
  background: #faf0ca;
}
</style>
