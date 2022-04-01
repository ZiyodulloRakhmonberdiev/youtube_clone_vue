<template>
  <span :class="classes" @mouseenter="toggleBadge" @mouseleave="toggleBadge">
    <BaseIcon :name="icon" class="w-5 h-5" />
    <span :class="badgeClasses">
      <span class="inline-block my-1.5 mx-3">{{ label }}</span>
    </span>
  </span>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
export default {
  components: {
    BaseIcon,
  },
  data() {
    return {
      isBadgeShown: false,
    };
  },
  props: {
    label: String,
    icon: String,
  },
  computed: {
    classes() {
      return [
        "opacity-0",
        "group-hover:opacity-100",
        "duration-100",
        "bg-opacity-60",
        "absolute",
        "right-0",
        "bg-black",
        "text-white",
        "m-1",
        "p-1",
        this.isBadgeShown ? "rounded-l-0" : "rounded-sm",
      ];
    },
    badgeClasses() {
      return [
        "absolute",
        "top-0",
        "transition-width",
        "bg-black ",
        "bg-opacity-60",
        "whitespace-nowrap",
        "right-full",
        "overflow-hidden",
        "uppercase",
        "text-gray",
        "text-xs",
        "delay-100",
        "font-semibold",
        "rounded-l-sm",
        this.isBadgeShown ? "w-28" : "w-0",
      ];
    },
  },
  methods: {
    toggleBadge() {
      this.isBadgeShown = !this.isBadgeShown;
    },
  },
};
</script>