<template>
  <div
    class="show-box clickable"
    :style="`background-image: url(${data.featureImage})`"
  >
    <q-card class="show-card bg-primary text-white">
      <div
        class="show-gif"
        :style="`background-image: url(${data.featureImage})`"
      />
      <q-card-section>
        <div class="row justify-between items-center">
          <div>
            <q-icon
              class="show-icon q-mr-sm bg-white"
              color="black"
              :class="!!!data.demoLink && 'icon-disabled'"
              name="fa fa-play"
              size="1.2rem"
              :aria-disabled="!!data.demoLink"
              @click="() => redirectPage(data.demoLink)"
            >
              <q-tooltip
                transition-show="scale"
                class="tool-tip"
                transition-hide="scale"
                >{{ data.demoLink ? "Try it" : "Not Available" }}</q-tooltip
              >
            </q-icon>
            <q-icon
              class="show-icon"
              color="white"
              name="fa fa-code"
              size="1.2rem"
              @click="() => redirectPage(data.githubLink)"
            >
              <q-tooltip
                transition-show="scale"
                class="tool-tip"
                transition-hide="scale"
                >Check Github</q-tooltip
              >
            </q-icon>
          </div>
          <div>
            <q-icon
              class="show-icon"
              color="white"
              name="fa fa-caret-down"
              size="1.2rem"
              @click="showDialog"
            >
              <q-tooltip
                transition-show="scale"
                class="tool-tip"
                transition-hide="scale"
                >Project & Info</q-tooltip
              >
            </q-icon>
          </div>
        </div>
      </q-card-section>
      <div class="q-px-md">
        <div class="row justify-between">
          <span class="text-sm">
            {{ data.name }}
          </span>
          <div class="row q-gutter-x-xs">
            <div v-for="(tech, i) in data.techStack" :key="i">
              <q-icon
                v-if="ICON_NAMES[tech]"
                :name="ICON_NAMES[tech].name"
                :color="ICON_NAMES[tech].color"
                size="1.5rem"
              />
            </div>
          </div>
        </div>
      </div>

      <!-- <q-card-section class="row q-gutter-x-sm" v-if="data.isWinner">
          <q-icon name="fa fa-crown" size="1rem" color="yellow" />
          <div class="text-uppercase">
            {{ data.isWinner.prize }}
          </div>
        </q-card-section> -->
      <!-- <q-card-section class="row q-gutter-x-sm">
        <q-badge
          outline
          :color="COLOR_TAGS[data.tagType].bgColor"
          :text-color="COLOR_TAGS[data.tagType].txtColor"
          >{{ data.tagType }}
        </q-badge>
        <div class="row q-gutter-x-xs">
          <div v-for="(tech, i) in data.techStack" :key="i">
            <q-icon
              v-if="ICON_NAMES[tech]"
              :name="ICON_NAMES[tech].name"
              :color="ICON_NAMES[tech].color"
              size="1.5rem"
            />
          </div> -->
      <!-- <q-icon
              v-if="ICON_NAMES[tech]"
              :name="ICON_NAMES[tech].name"
              size="2rem"
            /> -->
      <!-- </div>
      </q-card-section> -->
    </q-card>
  </div>
</template>

<script>
import { ICON_NAMES } from "src/utils/data";
import { useQuasar } from "quasar";
import ShowDialog from "./dialog/ShowDialog.vue";
export default {
  props: ["data"],

  setup(props) {
    const $q = useQuasar();
    const COLOR_TAGS = {
      Hackathon: {
        bgColor: "white",
        txtColor: "black",
      },
      "Side Project": {
        bgColor: "red",
        txtColor: "white",
      },
      Internship: {
        bgColor: "green",
        txtColor: "white",
      },
      Contract: {
        bgColor: "orange",
        txtColor: "white",
      },
    };
    function redirectPage(loc) {
      return loc && window.open(loc, "_blank");
    }
    function showDialog() {
      $q.dialog({
        component: ShowDialog,
        componentProps: {
          data: props.data,
        },
      })
        .onOk((loc) => {
          redirectPage(loc);
        })
        .onCancel(() => {});
    }
    return {
      ICON_NAMES,
      COLOR_TAGS,
      showDialog,
      redirectPage,
    };
  },
};
</script>

<style lang="scss" scoped>
.show-box {
  min-width: 17.5rem;
  min-height: 8.75rem;
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
.tool-tip {
  color: black;
  background-color: lightgrey;
}
.show {
  &-card {
    visibility: hidden;
    opacity: 0;
    transition: 0.2s ease-in;
    position: absolute;
    width: 100%;
    height: auto;
    z-index: 1;
  }
  &-gif {
    height: 50%;
    background-size: cover;
    background-position: center;
  }
  &-icon {
    border: 2px solid white;
    border-radius: 15px;
    padding: 6px;
  }
}
</style>
