<template>
  <div>
    <SidebarSection>
      <ul>
        <SidebarNavItem label="Home" icon="home" is-active />
        <SidebarNavItem label="Trending" icon="fire" />
        <SidebarNavItem label="Subscription" icon="collection" />
      </ul>
    </SidebarSection>
    <SidebarSection>
      <ul>
        <SidebarNavItem label="Library" icon="duplicate" />
        <SidebarNavItem label="History" icon="clock" />
      </ul>
    </SidebarSection>
    <SidebarSection class="px-8 py-4 border-b text-medium leading-5">
      <span class="text-sm">Sign in to like videos, comment and subscribe</span>
      <ButtonLogin
        class="
          flex
          items-center
          px-2
          py-0.5
          mt-3
          text-sm text-blue-700
          uppercase
          border border-blue-700
          rounded
        "
      />
    </SidebarSection>

    <SidebarSection class="py-2 border-b">
      <SidebarSectionHeading title="Best of YouTube" />
      <ul>
        <SidebarNavItem label="Music" icon="musicNote" />
        <SidebarNavItem label="Sports" icon="speakerphone" />
        <SidebarNavItem label="Gaming" icon="puzzle" />
        <SidebarNavItem label="Movies" icon="film" />
        <SidebarNavItem label="News" icon="newspaper" />
        <SidebarNavItem label="Live" icon="statusOnline" />
        <SidebarNavItem label="360&deg; Video" icon="eye" />
      </ul>
    </SidebarSection>
    <SidebarSection class="py-2 border-b">
      <ul>
        <SidebarNavItem label="Browse channels" icon="plusCircle" />
      </ul>
    </SidebarSection>
    <SidebarSection class="py-2 border-b">
      <div class="uppercase text-sm font-semibold px-6 py-2">More YouTube</div>
      <ul>
        <SidebarNavItem label="You Tube" icon="play" />
        <SidebarNavItem label="Live" icon="statusOnline" />
      </ul>
    </SidebarSection>
    <SidebarSection class="py-2 border-b">
      <SidebarSectionHeading title="More YouTube" />
      <ul>
        <SidebarNavItem label="Settings" icon="cog" />
        <SidebarNavItem label="Report history" icon="flag" />
        <SidebarNavItem label="Help" icon="questionMarkCircle" />
        <SidebarNavItem label="Send feedback" icon="annotation" />
      </ul>
    </SidebarSection>
    <SidebarSection class="px-6 py-4 text-xs font-semibold space-y-4">
      <TheFooter />
    </SidebarSection>
  </div>
</template>
<script>
import SidebarSection from "./SidebarSection.vue";
import SidebarNavItem from "./SidebarNavItem.vue";
import SidebarSectionHeading from "./SidebarSectionHeading.vue";
import ButtonLogin from "./ButtonLogin.vue";
import TheFooter from "./TheFooter.vue";
export default {
  components: {
    SidebarSection,
    SidebarNavItem,
    SidebarSectionHeading,
    ButtonLogin,
    TheFooter,
  },
};
</script>