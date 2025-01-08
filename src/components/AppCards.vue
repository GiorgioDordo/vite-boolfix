<script>
import {store} from '../store'
export default {
    data() {
        return {
            store,
            // flag: 'https://flagcdn.com/16x12/' + this.cardObject.original_language + '.png',
            // flag: 'fi fi-' + this.cardObject.original_language,
        }
    },
    props: {
    cardObject: {
      type: Object,
      required: true,
    }
  },
  }
</script>

<template>
    <div class="col-6 col-md-3 col-lg-2 mb-4">
        <article class="card w-100">
            <img :src="cardObject.poster_path" class="card-img-top" alt="">
        </article>
        <p>{{ cardObject.title }}</p>
        <p>{{ cardObject.original_title }}</p>
        <p :class="this.flag"></p>
        <p>{{ cardObject.release_date }}</p>
        <p>{{ cardObject.vote_average }}</p>
    </div>
</template>

<style lang="scss" scoped>
@use '../../node_modules/flag-icons/sass/flag-icons.scss';
</style>