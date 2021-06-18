<template>
  <v-row>
    <v-col cols="12">
      <v-card>
        <v-img height="250" :src="movie.backdrop_path"></v-img>

        <v-card-title
          >{{ movie.title }}
          <small class="ml-5"
            >({{ movie.runtime }}min) -
            {{ movie.release_date.split('-')[0] }}</small
          ></v-card-title
        >

        <v-card-text>
          <v-chip-group active-class="deep-purple accent-4 white--text" column>
            <v-chip v-for="genre in movie.genres" :key="genre.id">{{
              genre.name
            }}</v-chip>
          </v-chip-group>
        </v-card-text>

        <v-card-text> {{ movie.overview }}</v-card-text>

        <v-divider class="mx-4"></v-divider>

        <v-card-text>
          <p>Produzido por:</p>
          <small
            v-for="company in movie.production_companies"
            :key="company.id"
            class="d-block"
          >
            {{ company.name }}
          </small>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    movie: {
      release_date: '2020-01-01',
    },
  }),
  async fetch() {
    await this.$axios
      .get(`/movies/${this.$route.params.id}`)
      .then((response) => {
        this.movie = response.data
      })
      .catch((error) => {
        console.log('error: ' + error.response.data)
      })
  },
}
</script>
