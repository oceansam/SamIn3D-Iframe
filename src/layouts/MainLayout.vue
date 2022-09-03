<template>
  <div>
    <header class="flex justify-center">
      <header-section />
    </header>
    <div>
      <router-view />
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
// Components
import HeaderSection from "src/components/sections/HeaderSection.vue";

export default defineComponent({
  name: "MainLayout",
  components: {
    HeaderSection,
  },
  setup() {
    const inputField = ref();
    document.getElementsByTagName("body")[0].style.cursor =
      "url('cursor-test.png'), auto";

    return {
      inputField,
    };
  },
});
</script>
