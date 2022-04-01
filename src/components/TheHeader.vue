<template>
  <header :class="classes">
    <div class="lg:w-1/4 flex">
      <div
        :class="[
          'flex',
          'items-center',
          'xl:w-64',
          'lg:bg-white',
          'pl-4',
          isMobileSearchShown ? 'opacity-0' : 'opacity-100',
        ]"
      >
        <button
          @click="$emit('toggleSidebar')"
          class="mr-3 sm:ml-2 sm:mr-6 focus:outline-none"
        >
          <BaseIcon name="menu" />
        </button>
        <LogoMain />
      </div>
    </div>
    <TheSearchMobile v-if="isMobileSearchShown" @close="closeMobileSearch" />
    <div
      v-else
      class="
        hidden
        sm:flex
        p-2.5
        items-center
        lg:w-1/2
        flex-1
        max-w-screen-md
        justify-end
        md:pl-8 md:px-8
        lg:px-0
      "
    >
      <TheSearch />
      <BaseToolTip text="Search with your voice">
        <button class="p-2 focus:outline-none">
          <BaseIcon name="microphone" class="w-5 h-5" />
        </button>
      </BaseToolTip>
    </div>
    <div
      :class="[
        'flex',
        'items-center',
        'justify-end',
        'lg:w-1/4',
        'sm:space-x-3',
        'p-2',
        'sm:px-4',
        isMobileSearchShown ? 'opacity-0' : 'opacity-100',
      ]"
    >
      <BaseToolTip text="Search with your voice">
        <button class="sm:hidden p-2 focus:outline-none">
          <BaseIcon name="microphone" class="w-5 h-5" />
        </button>
      </BaseToolTip>
      <BaseToolTip text="Search">
        <button
          class="sm:hidden p-2 focus:outline-none"
          @click.stop="isMobileSearchActive = true"
        >
          <BaseIcon name="search" class="w-5 h-5" />
        </button>
      </BaseToolTip>
      <TheDropDownApps />
      <TheDropDownSettings />
      <ButtonLogin />
    </div>
  </header>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
import LogoMain from "./LogoMain.vue";
import BaseToolTip from "./BaseToolTip.vue";
import ButtonLogin from "./ButtonLogin.vue";
import TheSearch from "./TheSearch.vue";
import TheDropDownApps from "./TheDropDownApps.vue";
import TheDropDownSettings from "./TheDropDownSettings.vue";
import TheSearchMobile from "./TheSearchMobile.vue";
export default {
  components: {
    BaseIcon,
    LogoMain,
    BaseToolTip,
    ButtonLogin,
    TheSearch,
    TheDropDownApps,
    TheDropDownSettings,
    TheSearchMobile,
  },
  emits: {
    toggleSidebar: null,
  },
  computed: {
    isMobileSearchShown() {
      return this.isSmallScreen && this.isMobileSearchActive;
    },
  },
  data() {
    return {
      isSmallScreen: false,
      isMobileSearchActive: false,
      classes: [
        "flex",
        "bg-white",
        "bg-opacity-95",
        "w-full",
        "justify-between",
      ],
    };
  },
  mounted() {
    this.onResize();
    window.addEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      if (window.innerWidth < 640) {
        this.isSmallScreen = true;
        return;
      }
      this.isSmallScreen = false;
      this.closeMobileSearch();
    },
    closeMobileSearch() {
      this.isMobileSearchActive = false;
    },
  },
};
</script>