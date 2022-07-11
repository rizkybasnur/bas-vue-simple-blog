<template>
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
    :to="`/lists/${value.id}`"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      :src="`https://image.tmdb.org/t/p/original${value && value.poster_path}`"
    ></v-img>

    <v-card-title v-if="value && value.title">{{ value.title }}</v-card-title>
    <v-card-title v-if="value && value.name && !value.title">{{
      value.name
    }}</v-card-title>

    <v-card-text>
      <div class="text-truncate">
        Small plates, salads & sandwiches - an intimate setting with 12 indoor
        seats plus patio seating.
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "CardComponent",

  props: {
    value: {
      type: [Object, Array],
      default: () => {
        return {};
      },
    },
  },
};
</script>
