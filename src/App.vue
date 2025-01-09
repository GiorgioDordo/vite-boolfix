<script>
import AppHeader from './components/AppHeader.vue';
import AppCards from './components/AppCards.vue';
import "/node_modules/flag-icons/css/flag-icons.min.css";
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
            apiUrl: "https://api.themoviedb.org/3/search/movie",
            apiKey: "04f50f140d73590d28e01335e3f1bec8",
        }
    },
    methods: {
        getMovies (query) {
            console.log(query);
            axios.get(this.apiUrl, {
                params: {
                    api_key: this.apiKey,
                    query: query,
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

        // logInfo() {
        // // console.log("stringa da AppHeader arrivata ad App");
        // // stringa passata dallo store
        // console.log(`stringa arrivata da appheader${this.store.searchedInput}`);
        // },
    },
// non serve, dato che devo far partire la chiamata api solo dopo aver inserito un argomento nell'input search in AppHeader
//     created() {
//     this.getMovies();
//   },

}
</script>

<template>
<!-- Trasmetto la ricerca direttamente alla chiamata api -->
<AppHeader @searchedFilm="getMovies(store.searchedInput)"/>
<div class="container-fluid">
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
