<script setup lang="ts">
import { defineProps } from "vue";

// interface ButtonProps {
//   label: string;
//   iconPath?: string;
//   size: {
//     type: Number;
//     default: 1;
//     validator: (value: number) => [1, 2, 3, 4].includes(value as 1|2|3|4);,
//   };
// }

function classArray(): string {
  return `size-${props.size}`;
}

const props = defineProps({
  label: {
    type: String,
  },
  iconPath: {
    type: String,
    required: false,
  },
  size: {
    type: Number,
    default: 1,
    validator: (value: number) => [1, 2, 3, 4].includes(value as 1 | 2 | 3 | 4),
  },
});
</script>

<template>
  <div class="flex-auto flex-row">
    <button type="button" class="flex flex-row items-center" :size="classArray">
      {{ label }}
      <span v-if="iconPath" class="ml-4">
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
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
