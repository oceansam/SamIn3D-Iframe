<template>
  <div class="row justify-center items-center bg-primary q-py-xl">
    <div class="row">
      <div
        v-for="(text, i) in footer"
        :key="i"
        class="col-3 q-pa-sm text-grey text-center"
      >
        {{ text }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  setup() {
    const footer = [
      "Audio Description",
      "Investor Relations",
      "Legal Notices",
      "Help Center",
      "Jobs",
      "Cookie Preferences",
      "Gift Cards",
      "Terms of Use",
      "Corporate Information",
      "Media Center",
      "Privacy",
      "Contact Us",
    ];
    return { footer };
  },
};
</script>
