<template>
  <v-app>
    <v-content app>
      <Header />
      <router-view />
    </v-content>
  </v-app>
</template>
<style scoped></style>
<script>
import Header from "@/components/Header.vue";
export default {
  name: "App",
  components: {
    Header
  },
  data: () => ({
    //
  })
};
</script>
