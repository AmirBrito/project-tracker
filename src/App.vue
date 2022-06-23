<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <FormTracker @onSaveTask="saveTask" />
      <div class="taskList">
        <TaskTracker
          v-for="(task, index) in taskList"
          :key="index"
          :task="task"
        />
        <BoxTracker v-if="isEmptyList"> Start a task today! </BoxTracker>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import FormTracker from "./components/FormTracker.vue";
import TaskTracker from "./components/TaskTracker.vue";
import ITaskTracker from "./interfaces/ITaskTracker";
import BoxTracker from "./components/BoxTracker.vue";

export default defineComponent({
  name: "App",
  components: { SideBar, FormTracker, TaskTracker, BoxTracker },
  data() {
    return {
      taskList: [] as ITaskTracker[],
    };
  },
  computed: {
    isEmptyList(): boolean {
      return this.taskList.length === 0;
    },
  },
  methods: {
    saveTask(task: ITaskTracker) {
      this.taskList.push(task);
    },
  },
});
</script>

<style>
.taskList {
  padding: 1.25rem;
}
</style>
