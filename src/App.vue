<script>
import AppHeader from "./components/AppHeader.vue";
import axios from 'axios';
import store from './data/store.js'

export default {
  components: {
    AppHeader
  },
  data() {
    return {
      store,
      ricerca: ''
    }
  },
  methods: {
    getAxios() {
      const options = {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/search/movie',
        params: { query: this.ricerca, include_adult: 'false', language: 'en-US', page: '1' },
        headers: {
          accept: 'application/json',
          Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI2OGY1MzlkNGM1ZjRlYTEyZDEwMjg5NzFjMzU3MTgzOCIsInN1YiI6IjY2NTcyY2MxMmY5MjRlNzQwMDkzYjZiYyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.zHZRcfaBkWzhLUgDE3w4SNUZH_7KlESmXcfT9M45XyI'
        }
      };

      axios
        .request(options)
        .then(function (response) {
          console.log(response.data.results);
        })
        .catch(function (error) {
          console.error(error);
        });
    }


  },
  mounted() {
  }
}
</script>

<template>

  <AppHeader />

  <section id="cerca">
    <input v-model="ricerca" type="text" placeholder="Cerca">
    <span>{{ ricerca }}</span>
    <button @click="getAxios()">Invio</button>
  </section>

</template>

<style scoped></style>
