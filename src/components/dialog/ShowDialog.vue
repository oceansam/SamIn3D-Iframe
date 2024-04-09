<template>
  <q-dialog class="dialog" ref="dialogRef" @hide="onDialogHide">
    <q-card class="dialog-card bg-primary">
      <div
        class="show-gif"
        :style="`background-image: url(${data.featureImage})`"
      />
      <q-card-section class="row justify-between text-white">
        <div class="col">
          <div class="text-lg">
            {{ data.name }}
          </div>
          <div class="text-green text-capitalize text-xs">
            {{ data.field }}
          </div>
        </div>
        <div class="text-xs col">
          <div>
            <span class="text-grey">Tech stack: </span>
            <span v-for="tech in data.techStack" :key="tech">
              {{ tech }},&nbsp;
            </span>
          </div>
          <div>
            <span class="text-grey">Project type: </span>
            <span>
              {{ data.tagType }}
            </span>
          </div>
        </div>
      </q-card-section>
      <q-separator inset color="white" />
      <q-card-section class="text-white">
        <div class="text-xs">
          {{ data.description }}
        </div>
      </q-card-section>
      <q-card-section class="row q-gutter-x-md justify-end">
        <q-btn
          class="dialog-button"
          v-if="data.githubLink"
          @click="() => navTo(data.githubLink)"
          label="Source Code"
        />
        <q-btn
          class="dialog-button"
          v-if="data.devpostLink"
          @click="() => navTo(data.devpostLink)"
          label="Devpost Article"
        />
        <q-btn
          class="dialog-button"
          v-if="data.demoLink"
          @click="() => navTo(data.demoLink)"
          label="Demo"
        />
      </q-card-section>
    </q-card>
  </q-dialog>
</template>

<script>
import { useDialogPluginComponent } from "quasar";
import { useRouter } from "vue-router";
export default {
  props: ["data"],
  emits: {
    // REQUIRED; need to specify some events that your
    // component will emit through useDialogPluginComponent()
    ...useDialogPluginComponent.emitsObject,

    // ...your own definitions
  },
  setup(props) {
    const $r = useRouter();
    // REQUIRED; must be called inside of setup()
    const { dialogRef, onDialogHide, onDialogOK, onDialogCancel } =
      useDialogPluginComponent();
    // dialogRef      - Vue ref to be applied to QDialog
    // onDialogHide   - Function to be used as handler for @hide on QDialog
    // onDialogOK     - Function to call to settle dialog with "ok" outcome
    //                    example: onDialogOK() - no payload
    //                    example: onDialogOK({ /*.../* }) - with payload
    // onDialogCancel - Function to call to settle dialog with "cancel" outcome
    console.log(props);
    function navTo(location) {
      onDialogOK(location);
    }
    return {
      // This is REQUIRED;
      // Need to inject these (from useDialogPluginComponent() call)
      // into the vue scope for the vue html template
      dialogRef,
      onDialogHide,
      navTo,
      // other methods that we used in our vue html template;
      // these are part of our example (so not required)
      onOKClick() {
        // on OK, it is REQUIRED to
        // call onDialogOK (with optional payload)
        onDialogOK();
        // or with payload: onDialogOK({ ... })
        // ...and it will also hide the dialog automatically
      },

      // we can passthrough onDialogCancel directly
      onCancelClick: onDialogCancel,
    };
  },
};
</script>

<style lang="scss" scoped>
.dialog {
  &-card {
    width: 100%;
  }
  &-button {
    background-color: white;
    color: black;
    font-size: 1rem;
  }
}
.show-gif {
  height: 250px;
  background-size: cover;
  background-position: center;
}
</style>
