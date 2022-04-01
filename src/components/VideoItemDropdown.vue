<template>
  <div class="relative -mt-1 ml-auto">
    <button @click="toggle" :class="buttonClasses">
      <BaseIcon name="dotsVertical" class="w-5 h-5" />
    </button>
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
        <section class="py-2 bg-gray-100">
          <ul>
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
          </ul>
        </section>
      </div>
    </transition>
  </div>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
import VideoItemDropdownListItem from "./VideoItemDropdownListItem.vue";
export default {
  components: {
    BaseIcon,
    VideoItemDropdownListItem,
  },
  data() {
    return {
      isOpen: false,
      positionClasses: [],
    };
  },
  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.isOpen = false;
      }
    });
    // window.addEventListener("scroll", () => (this.isOpen = false));
  },
  watch: {
    isOpen() {
      // document.body.classList.toggle("overflow-hidden");
      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    },
  },
  computed: {
    buttonClasses() {
      return [
        "p-1",
        "duration-100",
        "text-gray-500",
        "hover:text-gray-700",
        "focus:outline-none",
        "group-hover:opacity-100",
        this.isOpen ? "opacity-100" : "opacity-0",
      ];
    },
    dropdownClasses() {
      return [
        "z-30",
        "bg-white",
        "absolute",
        "w-48",
        "rounded",
        "shadow",
        "outline-none",
        ...this.positionClasses,
      ];
    },
  },
  methods: {
    toggle(event) {
      this.isOpen = !this.isOpen;
      if (this.isOpen) {
        this.$nextTick(() => {
          this.positionClasses = this.getPositionClasses(event);
        });
      }
    },
    getPositionClasses(event) {
      return [
        this.getTopClass(event),
        this.getBottomClass(event),
        this.getRightClass(event),
        this.getLeftClass(event),
      ];
    },
    getTopClass(event) {
      const clickCoordY = event.clientY;
      const buttonHeight = event.currentTarget.offsetHeight;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;
      if (window.innerHeight - clickCoordY < dropdownHeight) {
        return "top-auto";
      }
      if (window.innerHeight - clickCoordY < dropdownHeight + buttonHeight) {
        return "top-0";
      }
      return "top-8";
    },
    getRightClass(event) {
      const clickCoordX = event.clientX;
      const clickCoordY = event.clientY;
      const buttonHeight = event.currentTarget.offsetHeight;
      const dropdownWidth = this.$refs.dropdown.offsetWidth;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;

      if (window.innerWidth - clickCoordX > dropdownWidth) {
        return "right-auto";
      }
      if (window.innerHeight - clickCoordY > dropdownHeight + buttonHeight) {
        return "right-0";
      }
      if (window.innerHeight - clickCoordY > dropdownHeight) {
        return "right-8";
      }
      return "right-0";
    },
    getLeftClass(event) {
      const clickCoordX = event.clientX;
      const clickCoordY = event.clientY;
      const buttonHeight = event.currentTarget.offsetHeight;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;
      const dropdownWidth = this.$refs.dropdown.offsetWidth;
      if (window.innerWidth - clickCoordX < dropdownWidth) {
        return "left-auto";
      }
      if (window.innerHeight - clickCoordY < dropdownHeight) {
        return "left-auto";
      }
      if (window.innerHeight - clickCoordY > dropdownHeight + buttonHeight) {
        return "left-auto";
      }
      return "left-8";
    },
    getBottomClass(event) {
      const clickCoordY = event.clientY;
      const buttonHeight = event.currentTarget.offsetHeight;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;
      if (window.innerHeight - clickCoordY < dropdownHeight) {
        return "bottom-8";
      }

      return "bottom-auto";
    },
  },
};
</script>