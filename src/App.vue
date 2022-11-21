<template>
  <v-app>
    <v-app-bar app>
      <router-link to="/">
        <v-toolbar-title>日向美術館</v-toolbar-title>
      </router-link>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer>
      <v-card-text>日向美術館</v-card-text>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    items: [
      { title: "Home", to: "/" },
      { title: "About", to: "/about" },
    ],
  }),
};
</script>

<style>
.v-application a:link,
.v-application a:visited,
.v-application a:hover,
.v-application a:active {
  color: #333333 !important;
  text-decoration: none;
}
.v-footer {
  font-size: 0.7rem;
}
</style>