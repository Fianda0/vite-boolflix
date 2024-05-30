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
        }
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
                <section class="imgCard"><img :src="getImg(element.backdrop_path)" alt=""></section>
                <section class="txtCard">
                    <p><span class="title">Titolo:</span> {{ element.title }}</p>
                    <br>
                    <p><span class="title">Titolo Originale:</span> {{ element.original_title }}</p>
                    <br>
                    <p>
                        <span class="title">Lingua:</span>
                        <span v-if="element.original_language == 'it'"><img
                                src="https://upload.wikimedia.org/wikipedia/commons/0/03/Flag_of_Italy.svg"
                                alt=""></span>
                        <span v-else-if="element.original_language == 'en'"><img
                                src="https://upload.wikimedia.org/wikipedia/commons/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg"
                                alt=""></span>
                        <span v-else>Non Definita</span>
                    </p>
                    <br>
                    <p><span class="title">Voto:</span> {{ element.vote_average }}</p>
                </section>
            </div>
        </div>
        <h2>Serie TV</h2>
        <div class="container-card">
            <div v-for="element in store.serie" class="card">
                <section class="imgCard"><img :src="getImg(element.backdrop_path)" alt=""></section>
                <section class="txtCard">
                    <p><span class="title">Titolo:</span> {{ element.title }}</p>
                    <br>
                    <p><span class="title">Titolo Originale:</span> {{ element.original_title }}</p>
                    <br>
                    <p>
                        <span class="title">Lingua:</span>
                        <span v-if="element.original_language == 'it'"><img
                                src="https://upload.wikimedia.org/wikipedia/commons/0/03/Flag_of_Italy.svg"
                                alt=""></span>
                        <span v-else-if="element.original_language == 'en'"><img
                                src="https://upload.wikimedia.org/wikipedia/commons/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg"
                                alt=""></span>
                        <span v-else>Non Definita</span>
                    </p>
                    <br>
                    <p><span class="title">Voto:</span> {{ element.vote_average }}</p>
                </section>
            </div>
        </div>
    </main>
</template>

<style scoped>
h2 {
    text-align: center;
    padding: 2rem;
}

.container-card {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.card {
    overflow: auto;
    border: 1px solid black;
    padding: 0.5rem;
    margin: 0.5rem;
    width: calc(100% / 5);
    height: 10rem;
}

.imgCard {
    height: 100%;
}

.txtCard {
    display: none;
}

.card:hover .txtCard {
    display: block;
}

.card:hover .imgCard {
    display: none;
}




.title {
    color: green;
    font-weight: bold;
}

img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
}

span img {
    width: 20px;
    height: 10px;
    margin-left: 1rem;
}
</style>
