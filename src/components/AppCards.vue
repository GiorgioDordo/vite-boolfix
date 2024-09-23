<script>
import AppFilms from './AppFilms.vue';
import axios from 'axios';

export default {
    components: {
        AppFilms,
    },
    data() {
        return{
            filmList: [],
            apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=04f50f140d73590d28e01335e3f1bec8',
        }
    },
    methods: {
        getFilms (searched = null) {
            axios.get(this.apiUrl, {
                params: {
                    num: 35,
                    offset: 0,
                    movie: searched, 
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
  <div class="container">
    <section class="container-card p-5 d-flex flex-column">
        <div class="row">
            <AppFilms v-for="cardFilms in filmList" :key="cardFilms.id" :cardObject="cardFilms" class="mb-4" />
        </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
</style>