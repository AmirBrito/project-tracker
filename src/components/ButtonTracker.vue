<template>
  <button class="button" @click="clicked" :disabled="isDisabled">
    <span class="icon">
      <fa :icon="iconButton" />
    </span>
    <span>{{ textButton }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "ButtonTracker.vue",
  emits: ["clicked"],
  props: {
    isDisabled: {
      type: Boolean,
    },
    iconButton: {
      type: String,
      required: true,
    },
    textButton: {
      type: String,
      required: true,
    },
  },
  methods: {
    clicked(): void {
      this.$emit("clicked");
    },
  },
});
</script>
