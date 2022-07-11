<template>
  <v-container fluid>
    <v-row dense>
      <v-col cols="12" class="pa-0">
        <div style="width: 100%">
          <v-img
            :src="`https://image.tmdb.org/t/p/original${infos.poster_path}`"
            width="100%"
            height="400"
          />
        </div>
      </v-col>
      <v-col
        cols="12"
        style="display: flex; flex-direction: column; align-items: center"
      >
        <h1>This is an {{ infos.original_title }} reviews page</h1>

        <div>{{ infos.overview }}</div>

        <div style="display: flex">
          <div v-for="social in socials" :key="social">
            <SocmedButton :value="social" />
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
import SocmedButton from "@/components/base/SocmedButton.vue";

export default {
  name: "DetailComponent",

  data: () => ({
    infos: null,
    socials: [
      {
        logo: "mdi-facebook",
        to: `https://www.facebook.com/share.php`,
      },
      { logo: "mdi-twitter", to: `https://twitter.com/intent/tweet?text=test` },
      {
        logo: "mdi-linkedin",
        to: `https://www.linkedin.com/sharing/share-offsite/?url=facebook.com`,
      },
    ],
  }),
  mounted() {
    axios
      .get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=1fc0226d70db0b1d92b9fc0d70b764b4`
      )
      .then((response) => {
        this.infos = response?.data;
        console.log(this.infos);
      });
  },
  components: { SocmedButton },
};
</script>
