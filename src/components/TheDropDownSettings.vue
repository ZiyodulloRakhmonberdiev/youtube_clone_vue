<template>
  <div class="relative">
    <BaseToolTip text="Settings">
      <button @click="toggle" class="relative p-2 focus:outline-none">
        <BaseIcon name="dotsVertical" class="w-5 h-5" />
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
        @keydown.esc="close"
        tabindex="-1"
        :class="dropdownClasses"
      >
        <TheDropDownSettingsMain
          v-if="selectedMenu === 'main'"
          @select-menu="showSelectedMenu"
        />
        <TheDropDownSettingsAppearance
          v-else-if="selectedMenu === 'appearance'"
          @select-menu="showSelectedMenu"
        />
        <TheDropDownSettingsLanguage
          v-else-if="selectedMenu === 'language'"
          @select-menu="showSelectedMenu"
        />
        <TheDropDownSettingsLocation
          v-else-if="selectedMenu === 'location'"
          @select-menu="showSelectedMenu"
        />
        <TheDropDownSettingsRestrictedMode
          v-else-if="selectedMenu === 'restricted_mode'"
          @select-menu="showSelectedMenu"
        />
      </div>
    </transition>
  </div>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
import BaseToolTip from "./BaseToolTip.vue";
import TheDropDownSettingsMain from "./TheDropDownSettingsMain.vue";
import TheDropDownSettingsAppearance from "./TheDropDownSettingsAppearance.vue";
import TheDropDownSettingsLanguage from "./TheDropDownSettingsLanguage.vue";
import TheDropDownSettingsLocation from "./TheDropDownSettingsLocation.vue";
import TheDropDownSettingsRestrictedMode from "./TheDropDownSettingsRestrictedMode.vue";
export default {
  components: {
    BaseIcon,
    BaseToolTip,
    TheDropDownSettingsMain,
    TheDropDownSettingsAppearance,
    TheDropDownSettingsLanguage,
    TheDropDownSettingsLocation,
    TheDropDownSettingsRestrictedMode,
  },
  data() {
    return {
      isOpen: false,
      selectedMenu: "main",
    };
  },
  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.close();
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
        "w-72",
        "border border-t-0",
        "outline-none",
      ];
    },
  },
  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    },
  },
  methods: {
    showSelectedMenu(selectedMenu) {
      this.selectedMenu = selectedMenu;
      this.$refs.dropdown.focus();
    },
    open() {
      this.isOpen = true;
    },
    close() {
      this.isOpen = false;
      this.selectedMenu = "main";
      setTimeout(() => (this.selectedMenu = "main"), 100);
    },
    toggle() {
      this.isOpen ? this.close() : this.open();
    },
  },
};
</script>