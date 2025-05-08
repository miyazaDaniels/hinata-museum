<template>
  <v-app>
    <v-app-bar app>
      <router-link to="/" class="ml-4">
        <v-toolbar-title class="app-title">日向美術館</v-toolbar-title>
      </router-link>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer>
      <v-card-text class="footer-text">&copy; 2022 日向美術館</v-card-text>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
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

.v-toolbar-title.app-title {
  font-family: 'Kaisei Opti', serif !important;
  font-size: 2rem !important;
  font-weight: 500 !important;
  line-height: 1.2 !important;
}

.footer-text {
  font-family: 'Kaisei Opti', serif;
  font-size: 0.7rem;
}
</style>