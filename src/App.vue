<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title class="mr-7">Memory Game</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container fluid> </v-container>
    </v-main>
    <v-footer color="primary" app>
      <span class="white--text"
        >George Beuhler &copy; {{ new Date().getFullYear() }}</span
      >
    </v-footer>
  </v-app>
</template>
<script>
export default {
  name: "App",
  components: {},
};
</script>
