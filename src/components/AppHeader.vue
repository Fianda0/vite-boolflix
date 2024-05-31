<script>
import axios from 'axios';
import store from '../data/store.js'

export default {
    data() {
        return {
            store,
            ricerca: '',
            tipe: ''
        }
    },
    methods: {

        getAxiosMovie() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                params: { query: this.ricerca, include_adult: 'false', page: '1' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI2OGY1MzlkNGM1ZjRlYTEyZDEwMjg5NzFjMzU3MTgzOCIsInN1YiI6IjY2NTcyY2MxMmY5MjRlNzQwMDkzYjZiYyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.zHZRcfaBkWzhLUgDE3w4SNUZH_7KlESmXcfT9M45XyI'
                }
            };

            axios.request(options).then(risultato => {
                store.film = risultato.data.results
            })
        },
        getAxiosTv() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/tv',
                params: { query: this.ricerca, include_adult: 'false', page: '1' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI2OGY1MzlkNGM1ZjRlYTEyZDEwMjg5NzFjMzU3MTgzOCIsInN1YiI6IjY2NTcyY2MxMmY5MjRlNzQwMDkzYjZiYyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.zHZRcfaBkWzhLUgDE3w4SNUZH_7KlESmXcfT9M45XyI'
                }
            };

            axios.request(options).then(risultato => {
                store.serie = risultato.data.results
            })
        }
    },
    mounted() {
    }
}
</script>

<template>
    <header>
        <h1>BoolzFLIX</h1>
        <section id="cerca">
            <input v-model="ricerca" type="text" placeholder="Cerca" @keyup.enter="getAxiosMovie(), getAxiosTv()">
        </section>
    </header>

</template>

<style scoped>
header {
    background-color: black;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
}

h1 {
    color: red;
}

input {
    padding: 0.5rem 1rem;
}
</style>
