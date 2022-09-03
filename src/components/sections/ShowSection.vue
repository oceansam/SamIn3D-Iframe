<template>
  <div class="bg-primary q-px-xl q-pa-md">
    <div class="row header">
      <div class="text-white text-md text-bold">Trending Projects</div>
    </div>
    <div class="row q-gutter-md q-mt-md">
      <show-box v-for="(project, i) in projects" :key="i" :data="project" />
    </div>
    <!-- Work experience -->
    <div class="row header q-mt-xl">
      <div class="text-white text-md text-bold">Work Experience</div>
    </div>
    <div class="row q-gutter-md q-mt-md">
      <feature-box v-for="(work, i) in workExperience" :key="i" :data="work" />
    </div>
    <!-- <div class="row q-gutter-md q-mt-md">
      <feature-box
        v-for="(work, i) in workExperience"
        :key="i"
        :data="workExperience"
      />
    </div> -->
    <div class="q-my-xl" />
  </div>
</template>

<script>
import ShowBox from "../ShowBox.vue";
import FeatureBox from "../FeatureBox.vue";
import { projects, workExperience } from "src/utils/data";
export default {
  components: {
    ShowBox,
    FeatureBox,
  },
  setup() {
    return {
      workExperience,
      projects,
    };
  },
};
</script>
