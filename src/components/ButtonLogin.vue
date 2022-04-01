<template>
  <button :class="classes">
    <BaseIcon name="userCircle" class="mr-2 h-7 w-7" />
    Sign in
  </button>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
export default {
  components: {
    BaseIcon,
  },
  computed: {
    classes() {
      return (
        this.$attrs.class ||
        "flex items-center px-2 py-1 text-sm text-blue-700 uppercase border border-blue-700 rounded whitespace-nowrap"
      );
    },
  },
};
</script>