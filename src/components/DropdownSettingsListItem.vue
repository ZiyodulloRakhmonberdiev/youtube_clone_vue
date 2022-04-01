<template>
  <li>
    <a href="#" class="flex items-center px-3 py-2 text-sm hover:bg-gray-100">
      <BaseIcon
        v-if="isIconShown"
        :name="iconName"
        class="w-5 h-5 mr-3 text-gray-400"
      />
      <span :class="['truncate flex-1', { 'ml-8': !isIconShown }]">{{
        label
      }}</span>
      <BaseIcon
        v-if="withSubMenu"
        name="chevronRight"
        class="h-5 w-5 text-gray-400 ml-auto"
      />
    </a>
  </li>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
export default {
  components: {
    BaseIcon,
  },
  props: {
    active: Boolean,
    label: String,
    withSubMenu: Boolean,
    icon: {
      type: String,
      default: "check",
    },
  },
  computed: {
    isIconShown() {
      return this.active || this.icon !== "check";
    },
    iconName() {
      return this.active ? "check" : this.icon;
    },
  },
};
</script>