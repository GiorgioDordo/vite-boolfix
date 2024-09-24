<script>
import {store} from '../store'
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
  }
}
</script>

<template>
    <div class="col-6 col-md-3 col-lg-2 mb-4">
        <article class="card w-100">
            <img :src="cardObject.poster_path" class="card-img-top" alt="">
        </article>
        <p>{{ cardObject.title }}</p>
        <p>{{ cardObject.original_title }}</p>
        <p>{{ cardObject.original_language }}</p>
        <p>{{ cardObject.vote_average }}</p>
    </div>
</template>

<style lang="scss" scoped>
</style>