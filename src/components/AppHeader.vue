<script>
import {store} from '../store'

export default {
    data () {
        return {
            store,
            inputFilm: '',
        }
    },
    // creo un metodo per ricevere la stringa data da input e stamparla in console
    methods: {
        inputMessage(message) {
            console.log(message);
            this.$emit("searchedFilm");
        },
    }
}
</script>

<template>
<header class="d-flex justify-content-between align-items-center">
        <ul class="list-unstyled d-flex align-items-center gap-3">
            <li class="boolflix">BOOLFLIX</li>
            <li>Home</li>
            <li>TV Shows</li>
            <li>Movies</li>
            <li>New & Popular</li>
            <li>My List</li>
            <li>Browse by Languages</li>
        </ul>

        <!-- Creo un input per poter ricevere un argomento che poi usero per la mia ricerca api -->
        <div class="d-flex">
            <input type="text" placeholder="search" @keyup.enter="inputMessage(inputFilm)" v-model="inputFilm">
        </div>
</header>
</template>

<style lang="scss" scoped>

header {
    height: 70px;
    background-color: black;
    color: white;
    padding: 0 40px 0 40px;

    ul {
        margin: 0;

       .boolflix {
        color: red;
        font-size: 30px;
    }
    }
}
</style>