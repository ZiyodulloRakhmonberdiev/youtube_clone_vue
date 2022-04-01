<template>
  <div>
    <transition
      enter-active-class="transition-opacity ease-linear duration-200"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-opacity ease-linear duration-200"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <SidebarMobileOverlay @click="$emit('close')" v-show="isOpen" />
    </transition>
    <transition
      enter-active-class="transition ease-in-out transform duration-200"
      enter-from-class="-translate-x-full"
      enter-to-class="translate-x-0"
      leave-active-class="transition ease-in-out transform duration-200"
      leave-from-class="translate-x-0"
      leave-to-class="-translate-x-full"
    >
      <aside
        v-show="isOpen"
        @keydown.esc="$emit('close')"
        ref="mobileSidebar"
        tabindex="-1"
        class="w-64 fixed max-h-screen z-40 overflow-auto bg-white outline-none"
      >
        <section class="flex items-center p-4 border-b sticky top-0 bg-white">
          <button class="ml-2 mr-6 focus:outline-none" @click="$emit('close')">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-6 w-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M4 6h16M4 12h16M4 18h16"
              />
            </svg>
          </button>
          <LogoMain />
        </section>
        <SidebarContent />
      </aside>
    </transition>
  </div>
</template>
<script>
import LogoMain from "./LogoMain.vue";
import SidebarContent from "./SidebarContent.vue";
import SidebarMobileOverlay from "./SidebarMobileOverlay.vue";
export default {
  components: {
    LogoMain,
    SidebarContent,
    SidebarMobileOverlay,
  },
  props: {
    isOpen: Boolean,
  },
  emits: {
    close: null,
  },
  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.mobileSidebar.focus());
    },
  },
};
</script>