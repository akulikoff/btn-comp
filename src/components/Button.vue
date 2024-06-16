<script setup lang="ts">
import { defineProps, computed } from "vue";

// interface ButtonProps {
//   label: string;
//   iconPath?: string;
//   size: {
//     type: Number;
//     default: 1;
//     validator: (value: number) => [1, 2, 3, 4].includes(value as 1|2|3|4);,
//   };
// }
type IconPos<T extends "left" | "right"> = T;

const classArray = computed((): string[] => {
  return [`size-${props.size}`, `text-${props.color}`, `bg-${props.bgColor}`];
});
const iconPosition = computed(() => {
  return props.iconPosition ? "order-first" : "order-last";
});
const props = defineProps({
  label: {
    type: String,
  },
  iconPath: {
    type: String,
    required: false,
  },
  iconPosition: {
    type: String as () => IconPos<"left" | "right">,
    default: "left",
  },
  size: {
    type: Number,
    default: 4,
    validator: (value: number) => [1, 2, 3, 4].includes(value as 1 | 2 | 3 | 4),
  },
  bgColor: {
    type: String,
    required: true,
    default: "indigo-500",
  },
  color: {
    type: String,
    required: true,
    default: "#fff",
  },
});
</script>

<template>
  <button
    type="button"
    class="flex flex-row items-center gap-2 px-4 min-w-max"
    :class="classArray"
  >
    <span v-if="label" class="">{{ label }}</span>
    <span v-if="iconPath" :class="iconPosition">
      <svg
        aria-hidden="true"
        viewBox="0 0 24 24"
        fill="currentColor"
        class="w-6 h-6"
      >
        <path :d="iconPath"></path>
      </svg>
    </span>
  </button>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
.size-1 {
  height: 20px;
}
.size-2 {
  height: 48px;
}
</style>
