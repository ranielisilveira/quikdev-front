<template>
  <v-app dark>
    <v-app-bar fixed app>
      <v-toolbar-title> TMDb - The MovieDatabase </v-toolbar-title>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer app>
      <span>Ranieli Silveira &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data: () => ({}),
}
</script>
