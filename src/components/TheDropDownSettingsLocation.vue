<template>
  <div>
    <DropdownSettingsHeader
      title="Choose your location"
      @back="$emit('select-menu', 'main')"
    />
    <section class="py-2">
      <ul class="max-h-96 overflow-auto">
        <DropdownSettingsListItem
          v-for="(locationName, locationId) in locations"
          :key="locationId"
          :label="locationName"
          :active="locationId === selectedLocationId"
          @click="selectedLocationId = locationId"
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
      selectedLocationId: 0,
      locations: [
        "Great Britain",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Russia",
        "Uzbekistan",
      ],
    };
  },
  emits: ["select-menu"],
};
</script>