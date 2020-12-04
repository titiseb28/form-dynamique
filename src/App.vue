<template>
  <v-app>
    <v-main>
      <fIndentity />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {
    fIndentity: () => import("./components/fIdentity"),
  },

  data: () => ({
    //
  }),
};
</script>
