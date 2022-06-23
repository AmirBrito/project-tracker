<template>
  <BoxTracker>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || "Task default" }}
      </div>
      <div class="column">
        <StopWatch :time-in-seconds="task.durationInSeconds" />
      </div>
    </div>
  </BoxTracker>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import StopWatch from "./StopWatch.vue";
import ITaskTracker from "../interfaces/ITaskTracker";
import BoxTracker from "./BoxTracker.vue";

export default defineComponent({
  name: "TaskTracker",
  components: {
    StopWatch,
    BoxTracker,
  },
  props: {
    task: {
      type: Object as PropType<ITaskTracker>,
      required: true,
    },
  },
});
</script>

<style></style>
