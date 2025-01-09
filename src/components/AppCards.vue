<script>
import {store} from '../store';

export default {
    data() {
        return {
            store,
        }
    },
    props: {
    cardObject: {
      type: Object,
      required: true,
    }
  },
  computed: {
    posterUrl() {
        // this is the base url for the images from the API documentation of TMDB
      return `https://image.tmdb.org/t/p/w500${this.cardObject.poster_path}`;
    },

    flagIcon() {
        if (this.cardObject.original_language === 'en') {
            return 'gb';
        } else if (this.cardObject.original_language === 'ja') {
            return 'jp'
        } else if (this.cardObject.original_language === 'ko') {
            return 'kr';
        } else if (this.cardObject.original_language === 'zh') {
            return 'cn';
        } else if (this.cardObject.original_language === 'sh' || this.cardObject.original_language === 'sr') {
            return 'rs';
        } else {    
            return this.cardObject.original_language;
        }
    }
  }
  }
</script>

<template>
    <div class="col-6 col-md-3 col-lg-2 mb-4">
        <article class="card w-100">
            <img :src="posterUrl" class="card-img-top" alt="">
        </article>
        <p>{{ cardObject.title }}</p>
        <p>{{ cardObject.original_title }}</p>
        <span :class="`fi fi-${flagIcon}`"></span>
        <p>{{ cardObject.release_date }}</p>
        <p>{{ cardObject.vote_average }}</p>
    </div>
</template>

<style lang="scss" scoped>
 
</style>