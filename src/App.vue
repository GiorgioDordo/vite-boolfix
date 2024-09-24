<script>
import AppHeader from './components/AppHeader.vue';
import AppCards from './components/AppCards.vue';
import axios from 'axios';

export default {
  components: {
    AppHeader,
    AppCards,
  },
    data() {
        return{
            filmList: [],
            apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=04f50f140d73590d28e01335e3f1bec8&query=ritorno+al+futuro',
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
        }
    },

    created() {
    this.getFilms();
  },

}
</script>

<template>
<AppHeader/>
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
