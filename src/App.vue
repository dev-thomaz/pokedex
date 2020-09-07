<template>
<div id="app">
    <div class="container">
        <img src="./assets/pokedex.png" alt="">
        <div class="columns is-multiline">
            <div v-for="(poke, index) in pokemons" :key="index" class="column is-4">
                <Pokemon :name="poke.name" :url="poke.url" :num="index+1" />
            </div>
        </div>
    </div>
</div>
</template>

<script>
import axios from "axios";
import Pokemon from "./components/Pokemon";
export default {
    name: "App",
    data() {
        return {
            pokemons: [],
        };
    },
    created: function () {
        axios
            .get(" https://pokeapi.co/api/v2/pokemon?limit=721&offset=0")
            .then((resp) => {
                this.pokemons = resp.data.results;
            });
    },
    components: {
        Pokemon,
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;

}
</style>
