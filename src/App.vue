<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from 'axios';
import store from './data/store.js'

export default {
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store,
      ricerca: '',
      tipe: ''
    }
  },
  methods: {

  },
  mounted() {
  }
}
</script>

<template>

  <AppHeader />

  <AppMain />

</template>

<style scoped></style>
