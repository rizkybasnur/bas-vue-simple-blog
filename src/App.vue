<template>
  <v-app>
    <v-app-bar app color="gray darken-1" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          :src="require('../src/assets/logo.png')"
          transition="scale-transition"
          width="40"
          to="/"
        />

        <div>Movies Blogs</div>
      </div>

      <v-spacer></v-spacer>

      <v-tabs background-color="transparent">
        <v-tab to="/">Home</v-tab>
        <v-tab to="/lists">Review Lists</v-tab>
      </v-tabs>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
};
</script>
