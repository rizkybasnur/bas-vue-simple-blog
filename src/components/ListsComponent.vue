<template>
  <v-container fluid>
    <v-row v-if="isLoading">
      <v-col cols="12" style="display: flex; justify-content: center">
        <v-progress-circular
          indeterminate
          color="primary"
        ></v-progress-circular>
      </v-col>
    </v-row>

    <v-row v-if="!isLoading" dense>
      <v-col cols="12" style="display: flex; justify-content: center">
        <v-card-title>MOVIE LISTS</v-card-title>
      </v-col>
      <v-col v-for="(item, i) in infos" :key="'item' + i" cols="12" md="3">
        <Card :value="item" />
      </v-col>
    </v-row>

    <div class="text-center">
      <v-pagination v-model="page" :length="6" @input="next"></v-pagination>
    </div>
  </v-container>
</template>

<script>
import axios from "axios";
import Card from "@/components/base/Card.vue";

export default {
  name: "ListsComponent",
  components: { Card },

  data() {
    return {
      infos: [],
      isLoading: false,
      page: 1,
    };
  },
  mounted() {
    this.fetchLists(1);
  },
  methods: {
    fetchLists(page) {
      this.isLoading = true;
      axios
        .get(
          `https://api.themoviedb.org/3/trending/all/day?api_key=1fc0226d70db0b1d92b9fc0d70b764b4&page=${page}`
        )
        .then((response) => {
          this.infos = response?.data?.results;
          this.isLoading = false;
        });
    },
    next(page) {
      this.fetchLists(page);
      this.$router.push({
        query: { page: this.page },
      });
    },
  },
};
</script>
