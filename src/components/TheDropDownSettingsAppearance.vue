<template>
  <div>
    <DropdownSettingsHeader
      title="Appearance"
      @back="$emit('select-menu', 'main')"
    />
    <section class="py-2">
      <div class="text-gray-500 text-xs p-3">
        Setting applies to this browser only
      </div>
      <ul>
        <DropdownSettingsListItem
          v-for="(themeName, themeId) in themes"
          :key="themeId"
          :label="themeName"
          :active="themeId === selectedThemeId"
          @click="selectedThemeId = themeId"
        />
      </ul>
    </section>
  </div>
</template>
<script>
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";
import DropdownSettingsListItem from "./DropdownSettingsListItem.vue";
export default {
  components: {
    DropdownSettingsHeader,
    DropdownSettingsListItem,
  },
  data() {
    return {
      selectedThemeId: 0,
      themes: ["Use device theme", "Dark theme", "Light theme"],
    };
  },
  emits: ["select-menu"],
};
</script>