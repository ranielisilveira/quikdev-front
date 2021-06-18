<template>
  <v-row>
    <v-col v-for="movie in movies" :key="movie.id" md="3" sm="12">
      <nuxt-link :to="`/movies/${movie.id}`">
        <v-card max-width="374">
          <v-img height="250" :src="movie.poster"></v-img>

          <v-card-title>{{ movie.name }}</v-card-title>

          <v-card-text> {{ movie.overview.substr(0, 100) }}... </v-card-text>

          <v-divider class="mx-4"></v-divider>
        </v-card>
      </nuxt-link>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    movies: [],
  }),
  async fetch() {
    await this.$axios
      .get('/movies/trending')
      .then((response) => {
        this.movies = response.data
      })
      .catch((error) => {
        console.log('error: ' + error.response.data)
      })
  },
}
</script>
<style>
.v-application a {
  text-decoration: none;
}
</style>
