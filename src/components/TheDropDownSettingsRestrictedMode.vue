<template>
  <div>
    <DropdownSettingsHeader
      title="Appearance"
      @back="$emit('select-menu', 'main')"
    />
    <section class="py-4 px-3 text-black text-sm space-y-4">
      <p>
        This helps hide potentially mature videos. No filter is 100% accurate
      </p>
      <p>This setting only applies to this browser.</p>
      <div class="text-gray-600 font-semibold flex items-center">
        <span class="uppercase mr-2">Active restricted mode</span>
        <input type="checkbox" />
      </div>
    </section>
  </div>
</template>
<script>
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";
export default {
  components: {
    DropdownSettingsHeader,
  },
  emits: ["select-menu"],
};
</script>