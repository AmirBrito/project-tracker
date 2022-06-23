<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">Task Description</div>
      <div class="column">
        <StopWatch :time-in-seconds="15" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopWatch from "./StopWatch.vue";

export default defineComponent({
  name: "TaskTracker",
  components: {
    StopWatch,
  },
});
</script>

<style scoped>
.box {
  background: #faf0ca;
}
</style>
