<script setup lang="ts">
import { defineProps, computed } from "vue";

type IconPos = "left" | "right";
type ColorType<T extends "indigo-700" | "stone-700" | "red-500" | "white"> = T;
type ButtonShadow = "shadow-md" | "shadow-lg" | "shadow-xl" | "shadow-2xl";
type FontSize<
  T extends
    | "text-sm"
    | "text-base"
    | "text-lg"
    | "text-xl"
    | "text-2xl"
    | "text-3xl"
> = T;
enum ButtonSize {
  "leading-1" = 1,
  "leading-2" = 2,
  "leading-3" = 3,
  "leading-4" = 4,
  "leading-5" = 5,
  "leading-6" = 6,
  "leading-7" = 7,
  "leading-8" = 8,
  "leading-9" = 9,
  "leading-10" = 10,
  "leading-tight" = 11,
  "leading-snug" = 12,
  "leading-normal" = 13,
  "leading-relaxed" = 14,
  "leading-loose" = 15,
}
const classArray = computed((): string[] => {
  return [
    `leading-${props.lineHeight}`,
    `text-${props.color}`,
    `bg-${props.bgColor}`,
    `${props.fontSize}`,
    `size-${props.size}`,
    `${props.shadow}`,
  ];
});
// const BtnSizeSquare = computed(() => {
//   if (!props.label) return `w-24 h-24`;
// });
const iconPosition = computed(() => {
  return props.iconPosition === "left" ? "order-first" : "order-last";
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
    type: String as () => IconPos,
    default: "left",
  },
  lineHeight: {
    type: Number as () => ButtonSize,
    default: 4,
  },
  bgColor: {
    type: String as () => ColorType<
      "indigo-700" | "stone-700" | "red-500" | "white"
    >,
    required: true,
    default: "indigo-700",
  },
  color: {
    type: String as () => ColorType<
      "indigo-700" | "stone-700" | "red-500" | "white"
    >,
    required: true,
    default: "white",
  },
  size: {
    type: Number,
  },
  fontSize: {
    type: String as () => FontSize<
      "text-sm" | "text-base" | "text-lg" | "text-xl" | "text-2xl" | "text-3xl"
    >,
    default: "text-sm",
  },
  shadow: {
    type: String as () => ButtonShadow,
  },
});
</script>

<template>
  <button
    type="button"
    class="flex flex-row justify-center items-center gap-6 min-w-max rounded"
    :class="classArray"
  >
    <span v-if="label">{{ label }}</span>
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
