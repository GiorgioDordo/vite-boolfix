<script>
export default {
  data () {
    return {
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
  <div class="col-6 col-md-3 col-lg-2">
    <article class="card w-100">
        <img :src="cardObject.poster_path" class="card-img-top" alt="">
    </article>
    <p>{{ cardObject.title }}</p>
</div>
</template>

<style lang="scss" scoped>
img {
    height: 100px;
}
</style>