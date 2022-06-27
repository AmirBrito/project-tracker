<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="" />
    </h1>
    <button class="button" @click="changeMode">{{ darkModeButtonText }}</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
  emits: ["onChangeMode"],
  data() {
    return {
      darkModeActivated: false,
    };
  },
  computed: {
    darkModeButtonText() {
      if (this.darkModeActivated) {
        return "Dark mode OFF";
      }
      return "Dark mode ON";
    },
  },
  methods: {
    changeMode() {
      this.darkModeActivated = !this.darkModeActivated;
      this.$emit("onChangeMode", this.darkModeActivated);
    },
  },
});
</script>

<style>
header {
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
