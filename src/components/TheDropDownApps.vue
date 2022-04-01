<template>
  <div class="relative">
    <BaseToolTip text="YouTube apps">
      <button @click="isOpen = !isOpen" class="relative p-2 focus:outline-none">
        <BaseIcon name="viewGrid" class="w-5 h-5" />
      </button>
    </BaseToolTip>
    <transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transition opacity-0 scale-95"
      enter-to-class="transition opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-from-class="transition opacity-100 scale-100"
      leave-to-class="transition opacity-0 scale-95"
    >
      <div
        v-show="isOpen"
        ref="dropdown"
        @keydown.esc="isOpen = false"
        tabindex="-1"
        :class="dropdownClasses"
      >
        <section class="py-2 border-b">
          <ul>
            <DropdownAppsListItem label="YouTube TV" />
          </ul>
        </section>
        <section class="py-2 border-b">
          <ul>
            <DropdownAppsListItem label="YouTube Music" />
            <DropdownAppsListItem label="YouTube Kids" />
          </ul>
        </section>
        <section class="py-2 border-b">
          <ul>
            <DropdownAppsListItem label="Creator academy" />
            <DropdownAppsListItem label="YouTube for Artists" />
          </ul>
        </section>
      </div>
    </transition>
  </div>
</template>
<script>
import BaseToolTip from "./BaseToolTip.vue";
import DropdownAppsListItem from "./DropdownAppsListItem.vue";
import BaseIcon from "./BaseIcon.vue";
export default {
  components: {
    BaseIcon,
    DropdownAppsListItem,
    BaseToolTip,
  },
  data() {
    return {
      isOpen: false,
    };
  },
  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.isOpen = false;
      }
    });
  },
  computed: {
    dropdownClasses() {
      return [
        "z-10",
        "bg-white",
        "absolute",
        "top-9",
        "right-0",
        "sm:right-0",
        "w-60",
        "border border-t-0",
        "-right-full",
        "outline-none",
      ];
    },
  },
  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    },
  },
};
</script>