<script>
import {store} from '../store'

export default {
    data () {
        return {
            store,
        }
    },
// Con questo metodo vado a spedire la ricerca al padre app.vue
    methods: {
        sendQuery() {
            // console.log(message);
            this.$emit("searchedFilm");
        },
    }
}
</script>

<template>
<header class="d-flex justify-content-between align-items-center">
        <ul class="list-unstyled d-flex align-items-center gap-3">
            <li class="boolflix">BOOLFLIX</li>
            <li class="section">Home</li>
            <li class="section">TV Shows</li>
            <li class="section">Movies</li>
            <li class="section">New & Popular</li>
            <li class="section">My List</li>
            <li class="section">Browse by Languages</li>
        </ul>

        <!-- Creo un input per poter ricevere un argomento che poi usero per la mia ricerca api -->
        <div class="d-flex">
            <input type="text" placeholder="search" @keyup.enter="sendQuery" v-model="store.searchedInput"> <!--tramite il v-model spedisca la stringa in store, dal quale poi posso prendere l'argomento e usarlo in app.vue-->
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

        .section{
         cursor: pointer;
    }

       .boolflix {
        color: red;
        font-size: 30px;
    }
    }
}
</style>