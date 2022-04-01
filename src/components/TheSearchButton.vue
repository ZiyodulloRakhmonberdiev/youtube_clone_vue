<template>
  <BaseToolTip text="Search">
    <button
      class="
        flex
        focus:outline-none
        items-center
        px-6
        py-1
        text-gray-600
        bg-gray-100
        border border-l-0 border-gray-300
        rounded-tr-sm rounded-br-sm
        hover:border-gray-200
        h-full
      "
    >
      <BaseIcon name="search" class="w-5 h-5" />
    </button>
  </BaseToolTip>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
import BaseToolTip from "./BaseToolTip.vue";
export default {
  components: {
    BaseIcon,
    BaseToolTip,
  },
};
</script>