<script setup lang="ts">
interface ButtonProps {
  label: string;
  iconPath?: string;
  //   size: {default: "small"; large: "large"}
}
defineProps<ButtonProps>();
</script>

<template>
  <div class="flex-auto flex-row">
    <button type="button" class="flex flex-row items-center">
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
