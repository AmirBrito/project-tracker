<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <FormTracker />
      <div class="taskList">
        <TaskTracker />
        <TaskTracker />
        <TaskTracker />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import FormTracker from "./components/FormTracker.vue";
import TaskTracker from "./components/TaskTracker.vue";

export default defineComponent({
  name: "App",
  components: { SideBar, FormTracker, TaskTracker },
});
</script>

<style>
.taskList {
  padding: 1.25rem;
}
</style>
