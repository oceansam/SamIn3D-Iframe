<template>
  <div
    class="row justify-between items-center q-pa-md q-pl-xl bg-primary text-white full-width"
  >
    <div class="row items-center q-gutter-x-xl">
      <q-img src="netflix_logo.png" width="120px" height="32px" />
      <div>Portfolio</div>
    </div>
    <div class="row items-center q-gutter-x-md">
      <q-icon name="search" size="2rem" />
      <q-icon name="notifications" size="2rem" />
      <q-btn-dropdown color="white" flat no-caps>
        <template v-slot:label>
          <div class="row items-center no-wrap">
            <q-img src="profiles/github_profile.jpg" width="2rem" />
          </div>
        </template>
        <q-list class="bg-primary text-white">
          <q-item
            clickable
            v-close-popup
            class="q-pa-md"
            v-for="(user, i) in userList"
            :key="i"
          >
            <q-item-section avatar>
              <q-avatar>
                <img :src="user.imgUrl" />
              </q-avatar>
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ user.name }}</q-item-label>
              <q-item-label class="text-grey" caption>{{
                user.alias
              }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-btn-dropdown>
    </div>
  </div>
</template>

<script>
export default {
  setup() {
    const userList = [
      {
        name: "Github",
        imgUrl: "profiles/github_profile.jpg",
        alias: "/oceansam",
      },
      {
        name: "Linkedin",
        imgUrl: "profiles/github_profile.jpg",
        alias: "/samee-chowdhury",
      },
      {
        name: "Resume",
        imgUrl: "profiles/github_profile.jpg",
        alias: "/google-drive",
      },
    ];
    return {
      userList,
    };
  },
};
</script>
