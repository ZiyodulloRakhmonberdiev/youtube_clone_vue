<template>
  <div class="flex items-start mt-3">
    <img
      :src="`https://picsum.photos/seed/avatar${index}/68`"
      class="mr-3 rounded-full w-9 h-9"
      alt=""
    />
    <div class="text-sm">
      <span class="font-semibold text-gray-800">Video title {{ index }}</span>
      <div class="mt-1 flex">
        <BaseToolTip :text="channelName" top>
          <div>{{ channelName }}</div>
        </BaseToolTip>
        <BaseToolTip text="Verified" top>
          <BaseIcon name="checkCircle" class="h-3. w-3.5 ml-1" />
        </BaseToolTip>
      </div>
      <div v-html="summary"></div>
    </div>
    <VideoItemDropdown />
  </div>
</template>
<script>
import BaseIcon from "./BaseIcon.vue";
import BaseToolTip from "./BaseToolTip.vue";
import VideoItemDropdown from "./VideoItemDropdown.vue";
export default {
  components: {
    BaseIcon,
    BaseToolTip,
    VideoItemDropdown,
  },
  data() {
    return {
      channelName: `Channel name ${this.index}`,
    };
  },
  props: ["index"],
  computed: {
    summary() {
      const days = this.index === 1 ? "day" : "days";
      return `${this.index}k views &middot; ${this.index} ${days} ago`;
    },
  },
};
</script>