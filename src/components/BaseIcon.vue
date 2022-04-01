<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    :class="$attrs.class || 'h-6 w-6'"
    fill="none"
    viewBox="0 -3 24 24"
    stroke="currentColor"
    stroke-width="2"
    v-html="path"
  ></svg>
</template>
<script>
import icons from "../icon";
export default {
  props: ["name"],
  data() {
    return {
      path: icons[this.name],
    };
  },
};
</script>