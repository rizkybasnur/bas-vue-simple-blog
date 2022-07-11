<template>
  <v-btn class="mx-4 black--text" icon :href="value.to" target="_blank">
    <v-icon size="24px">
      {{ value.logo }}
    </v-icon>
  </v-btn>
</template>

<script>
export default {
  name: "SocmedButtonComponent",

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
