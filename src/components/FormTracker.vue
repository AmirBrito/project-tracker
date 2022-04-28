<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Form to create new task">
        <input type="text" class="input" placeholder="Inform task to start:" />
      </div>
      <div class="column">
        <TimerTracker />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerTracker from "./TimerTracker.vue";

export default defineComponent({
  name: "FormTracker",
  components: {
    TimerTracker,
  },
});
</script>

<style></style>
