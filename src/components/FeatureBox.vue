<template>
  <div
    class="work-box clickable"
    :style="`background-image: url(${data.featureImage})`"
    @click="showDialog"
  />
</template>
<script>
export default {
  props: ["data"],
  setup() {
    function showDialog() {}
    return {
      showDialog,
    };
  },
};
</script>
<style lang="scss" scoped>
.work-box {
  min-width: 15rem;
  min-height: 30rem;
  background-position: center;
  background-size: cover;
  position: relative;

  border-radius: 5px;

  &:hover {
    .show-card {
      visibility: visible;
      opacity: 1;
      width: 300px;
      height: 220px;
      transform: scaleX(1.5) scaleY(1.5);
    }
  }
}
</style>
