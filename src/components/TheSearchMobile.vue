<template>
  <div class="absolute flex p-2 w-full z-10">
    <BaseToolTip text="Back" right @click="$emit('close')">
      <button class="p-2 focus:outline-none mr-2">
        <BaseIcon name="arrowLeft" class="w-5 h-5" />
      </button>
    </BaseToolTip>
    <TheSearch />
    <BaseToolTip text="Search with your voice" left>
      <button class="p-2 focus:outline-none">
        <BaseIcon name="microphone" class="w-5 h-5" />
      </button>
    </BaseToolTip>
  </div>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
import BaseToolTip from "./BaseToolTip.vue";
import TheSearch from "./TheSearch.vue";
export default {
  components: {
    BaseIcon,
    BaseToolTip,
    TheSearch,
  },
  mounted() {
    window.addEventListener("click", this.onClick);
    // this.$nextTick(() => this.$el.refs.search.focus());
  },
  beforeUnmount() {
    window.removeEventListener("click", this.onClick);
  },
  methods: {
    onClick(event) {
      if (!this.$el.contains(event.target)) {
        this.$emit("close");
      }
    },
  },
};
</script>