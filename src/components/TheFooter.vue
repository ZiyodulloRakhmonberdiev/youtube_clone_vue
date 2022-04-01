<template>
  <div>
    <div>
      <a v-for="link in links.slice(0, 7)" :key="link" href="#" class="mr-2">
        {{ link }}
      </a>
    </div>
    <div>
      <a v-for="link in links.slice(7)" :key="link" href="#" class="mr-2">
        {{ link }}
      </a>
      <a href="#" class="mr-2"></a>
      <a href="#" class="mr-2"> </a>
      <a href="#" class="mr-2"></a>
      <a href="#" class="mr-2"></a>
    </div>
    <div class="font-normal text-gray-500 mt-4">&copy; 2022 Google LLC</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      links: [
        "About",
        "Press",
        "Copyriht",
        "Contact",
        "Creators",
        "Advertise",
        "Developers",
        "Privacy",
        "Policy & Safety",
        "How YouTube works",
        "Test new features",
      ],
    };
  },
};
</script>