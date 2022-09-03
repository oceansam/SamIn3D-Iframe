<template>
  <div class="hero-container row q-pa-xl">
    <div class="col-5 q-mt-xl">
      <q-img src="header_hero.png" width="70%" />
      <div class="row items-center q-gutter-x-sm text-white">
        <div
          class="bg-secondary top-icon q-px-sm q-py-xs text-center text-bold"
        >
          <div class="text-xs">TOP</div>
          <div class="text-md q-mt-none">10</div>
        </div>
        <div class="text-bold text-md">
          #1 Fullstack Developer based in Toronto
        </div>
      </div>
      <div class="hero-desc text-white text-md q-pt-lg">
        Computer science student passionate about creating things. Experience in
        full stack development with a focus on the frontend.
      </div>
      <div class="row q-mt-md q-gutter-x-sm">
        <q-btn
          no-caps
          class="bg-white text-black q-px-lg"
          @click="$w.open(social.linkedin)"
        >
          <q-icon left name="fab fa-linkedin" size="3rem" />
          <div class="text-sm q-pl-sm">Linkedin</div>
        </q-btn>
        <q-btn
          no-caps
          class="transparent text-white q-px-lg"
          @click="$w.open(social.github)"
        >
          <q-icon left name="fab fa-github" size="3rem" />
          <div class="text-sm q-pl-sm">Github</div>
        </q-btn>
      </div>
    </div>
  </div>
</template>

<script>
import { social } from "src/utils/data";
export default {
  setup() {
    const $w = window;
    return {
      social,
      $w,
    };
  },
};
</script>
<style lang="scss" scoped>
.top-icon {
  width: min-content;
  border-radius: 5px;
  line-height: 1;
}
.hero {
  &-desc {
    width: 80%;
  }
}
</style>
