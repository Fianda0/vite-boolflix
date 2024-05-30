<script>
import store from '../data/store.js'

export default {
    data() {
        return {
            store,
        }
    },
    methods: {
        getImg(percorso) {
            let risultato = null
            if (percorso == null) {
                risultato = new URL('../assets/imgVuota.jpg', import.meta.url);
            } else {
                risultato = new URL('http://image.tmdb.org/t/p/w500/' + percorso, import.meta.url);
            }
            return risultato.href
        },
        getStars(voto) {
            let numero = voto / 2;
            let stelle = ''
            numero.toFixed(0)
            for (let index = 0; index < numero; index++) {
                stelle += store.stella
            }
            return stelle
        },

    },

    mounted() {
    }
}
</script>

<template>
    <main>
        <h2>Film</h2>
        <div class="container-card">
            <div v-for="element in store.film" class="card">
                <div><img :src="getImg(element.backdrop_path)" alt=""></div>
                <p><span class="title">Titolo:</span> {{ element.title }}</p>
                <br>
                <p><span class="title">Titolo Originale:</span> {{ element.original_title }}</p>
                <br>
                <p><span class="title">Lingua:</span> {{ element.original_language }}</p>
                <br>
                <p><span class="title">Voto:</span> {{ getStars(element.vote_average) }}</p><span></span>
            </div>
        </div>
        <h2>Serie TV</h2>
        <div class="container-card">
            <div v-for="element in store.serie" class="card">
                <p><span class="title">Titolo:</span> {{ element.title }}</p>
                <br>
                <p><span class="title">Titolo Originale:</span> {{ element.original_title }}</p>
                <br>
                <p><span class="title">Lingua:</span> {{ element.original_language }}</p>
                <br>
                <p><span class="title">Voto:</span> {{ element.popularity }}</p><span></span>
            </div>
        </div>
    </main>
</template>

<style scoped>
.container-card {
    width: 100%;
    overflow: auto;
    display: flex;
    flex-wrap: wrap;
}

.card {
    overflow: auto;
    border: 1px solid red;
    padding: 1rem;
    margin: 1rem;
    width: calc(100% / 5);
}

.title {
    color: green;
    font-weight: bold;
}

img {
    width: 100%;
}
</style>
