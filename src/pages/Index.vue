<template>
  <div class="test2 full-height">
    <hero-section />
    <show-section />
    <footer-section />
  </div>
</template>

<script>
import { defineComponent } from "vue";
import HeroSection from "src/components/sections/HeroSection.vue";
import ShowSection from "src/components/sections/ShowSection.vue";
import FooterSection from "src/components/sections/FooterSection.vue";

export default defineComponent({
  name: "PageIndex",
  components: {
    HeroSection,
    ShowSection,
    FooterSection,
  },
});
</script>
