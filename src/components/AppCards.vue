<script>
import AppFilms from './AppFilms.vue';

export default {
    components: {
        AppFilms,
    },
    data() {
        return{

        }
    }
}
</script>

<template>
  <div class="container">
    <section class="container-card p-5 d-flex flex-column">
        <div class="row">
            <AppFilms class="mb-4" />
        </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
</style>