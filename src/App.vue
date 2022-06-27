<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'dark-mode': darkModeActivated }"
  >
    <div class="column is-one-quarter">
      <SideBar @onChangeMode="changeTheme" />
    </div>
    <div class="column is-three-quarter main-content">
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
      darkModeActivated: false,
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
    changeTheme(darkModeActivated: boolean) {
      this.darkModeActivated = darkModeActivated;
    },
  },
});
</script>

<style>
.taskList {
  padding: 1.25rem;
}

main {
  --primary-bg: #fff;
  --primary-text: #000;
}

main.dark-mode {
  --primary-bg: #2b2d42;
  --primary-text: #ddd;
}

.main-content {
  background: var(--primary-bg);
}
</style>
