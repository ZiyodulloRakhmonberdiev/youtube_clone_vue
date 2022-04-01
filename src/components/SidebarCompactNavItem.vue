<template>
  <a href="#" :class="classes">
    <BaseIcon :name="icon" class="h-6 w-6 mb-1.5" />
    <span class="text-xs">{{ label }}</span>
  </a>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
export default {
  components: {
    BaseIcon,
  },
  props: {
    label: String,
    icon: String,
    isActive: Boolean,
  },
  computed: {
    classes() {
      return [
        this.isActive ? "text-red-500" : "text-gray-600",
        "flex",
        "items-center",
        "flex-col",
        "px-2",
        "py-5",
        "hover:bg-gray-100",
      ];
    },
  },
};
</script>