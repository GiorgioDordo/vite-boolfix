<script>
import AppHeader from './components/AppHeader.vue';
import AppCards from './components/AppCards.vue';
import {store} from './store'
import axios from 'axios';

export default {
  components: {
    AppHeader,
    AppCards,
  },
    data() {
        return{
            store,
            filmList: [],
            apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=04f50f140d73590d28e01335e3f1bec8&query=star+wars',
        }
    },
    methods: {
        getFilms () {
            axios.get(this.apiUrl, {
                params: {
                    num: 35,
                    offset: 0,
                }
            })
            .then((response) => {
                console.log(response.data.results);
                this.filmList = response.data.results;
            })
            .catch(function(error) {
                console.log(error);
            })
            .finally(() => {
                console.log("fine chiamata API")
            });
        },

        logInfo() {
        console.log("stringa da AppHeader arrivata ad App");
        },
    },

    created() {
    this.getFilms();
  },

}
</script>

<template>
<AppHeader @searchedFilm="logInfo"/>
<div class="container">
    <section class="container-card p-5 d-flex flex-column">
        <div class="row">
          <AppCards v-for="cardFilms in filmList" :key="cardFilms.id" :cardObject="cardFilms"/>
        </div>
    </section>
  </div>
</template>

<style lang="scss">
@use '../node_modules/bootstrap/scss/bootstrap.scss' as *;
@use './general.scss' as *;
</style>
