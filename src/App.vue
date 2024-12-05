<!-- src/App.vue -->
<template>
<div>
    <h1>Pokémon Search</h1>
    <input v-model="searchPokemon" type="text" placeholder="Buscar Pokémon">
    <button @click="searchPokemonByName">Buscar</button>
    <PokemonDetail v-if="pokemon" :pokemon="pokemon" />
</div>
</template>

<script>
import axios from 'axios';
import PokemonDetail from './components/PokemonDetail.vue';

export default {
    name: 'App',
    components: {
        PokemonDetail
    },
    data() {
        return {
            searchPokemon: '',
            pokemon: null
        }
    },
    methods: {
        async searchPokemonByName() {
            try {
                const response = await axios.get(`https://pokeapi.co/api/v2/pokemon/${this.searchPokemon}`);
                this.pokemon = response.data;
            } catch (error) {
                console.error(error);
            }
        }
    },
    mounted() {
        this.searchPokemon = 'pikachu';
        this.searchPokemonByName();
    }
}
</script>
