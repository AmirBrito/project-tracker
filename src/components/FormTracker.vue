<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Form to create new task">
        <input
          type="text"
          class="input"
          placeholder="Inform task to start:"
          v-model="description"
        />
      </div>
      <div class="column">
        <TimerTracker @timer-tracker-finished="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerTracker from "./TimerTracker.vue";

export default defineComponent({
  name: "FormTracker",
  emits: ["onSaveTask"],
  components: {
    TimerTracker,
  },
  data() {
    return {
      description: "",
    };
  },
  methods: {
    finishTask(timeElapsed: number): void {
      this.$emit("onSaveTask", {
        durationInSeconds: timeElapsed,
        description: this.description,
      });
      this.description = "";
    },
  },
});
</script>

<style></style>
