<script>
export default {
    data () {
        return {
        }
    },
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

        <div class="d-flex">
            <input type="text" placeholder="search">
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