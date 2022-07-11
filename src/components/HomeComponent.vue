<template>
  <v-container fluid>
    <v-row dense class="text-center">
      <v-col cols="12" class="pa-0">
        <div style="width: 100%">
          <v-img
            :src="`https://image.tmdb.org/t/p/original${infos[random].poster_path}`"
            width="100%"
            height="400"
          />
        </div>
      </v-col>

      <v-col class="mb-4">
        <v-row dense>
          <v-col v-for="(item, i) in infos" :key="'item' + i" cols="12" md="3">
            <Card :value="item" />
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
import Card from "@/components/base/Card";

export default {
  name: "HomeComponent",

  components: {
    Card,
  },

  data: () => ({
    infos: [],
  }),

  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/trending/all/day?api_key=1fc0226d70db0b1d92b9fc0d70b764b4"
      )
      .then((response) => {
        this.infos = response?.data?.results;
        console.log(this.infos);
      });
  },

  computed: {
    random() {
      var random;
      var max = 19;
      random = Math.floor(Math.random() * max); //Finds number between 0 - max
      return random;
    },
  },
};
</script>
