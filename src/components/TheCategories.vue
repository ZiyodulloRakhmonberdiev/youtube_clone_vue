<template>
  <section :class="classes">
    <div
      class="
        bg-white bg-opacity-95
        border-t border-b
        px-4
        m-auto
        max-w-screen-2xl
      "
    >
      <div class="py-3 flex space-x-3 overflow-auto text-sm whitespace-nowrap">
        <CategoryItem
          v-for="category in categories"
          :key="category"
          :category="category"
          :is-active="category === 'All'"
        />
      </div>
    </div>
  </section>
</template>
<script>
import CategoryItem from "./CategoryItem.vue";
export default {
  components: {
    CategoryItem,
  },
  data() {
    return {
      categories: [
        "All",
        "Trucks",
        "Tools",
        "Machines",
        "Engines",
        "Show",
        "Ships",
        "Road",
        "Tanks",
        "Building",
        "Mars",
        "Woodwoking",
        "Tractors",
        "Songs",
        "TV shows",
        "Football",
        "Planes",
        "Live",
        "Streets",
        "Math",
        "Programmimg",
      ],
    };
  },
  props: {
    isSidebarOpen: Boolean,
  },
  computed: {
    classes() {
      return [this.isSidebarOpen ? "xl:pl-64" : "md:pl-24"];
    },
  },
};
</script>