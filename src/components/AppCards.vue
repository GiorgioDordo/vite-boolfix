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
        switch (this.cardObject.original_language) {
        case "en":
            return "gb";
        case "ja":
            return "jp";
        case "ko":
            return "kr";
        case "zh":
            return "cn";
        case "sh" || "sr":
            return "rs";
        case "hi":
            return "in";

        default:
        return this.cardObject.original_language;
        }
    },

    fullStars() {
      return Math.floor(this.cardObject.vote_average / 2);
    },
    // if the remainder(resto) is greater or equal to 1, then we have a half star
    // italiano: in questa operazione viene calcolato il resto e se è maggiore o uguale a 1(siccome una stella contiene 2 voti), allora abbiamo mezza stella
    halfStars() {
      return this.cardObject.vote_average % 2 >= 1 ? 1 : 0;
    },
    // to calculate the empty stars, we subtract the full stars and the half stars from 5
    emptyStars() {
      return 5 - this.fullStars - this.halfStars;
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
        <span :class="`fi fi-${flagIcon}`"></span>
        <p>{{ cardObject.release_date }}</p>
        <p id="vote"><b>Vote</b> : 
            <i class="fa-solid fa-star" v-for="n in fullStars" :key="'full-' + n"></i>
      <i class="fa-solid fa-star-half-stroke" v-if="halfStars" :key="'half'"></i>
      <i class="fa-regular fa-star" v-for="n in emptyStars" :key="'empty-' + n"></i>
        </p>
    </div>
</template>

<style lang="scss" scoped>
 p {
     color: white;
 }
</style>