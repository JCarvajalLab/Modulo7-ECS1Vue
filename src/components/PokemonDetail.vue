<template>
<div class="card">
    <img :src="pokemon.sprites.front_default" alt="Pokémon Image" class="card-img-top">
    <div class="card-body">
        <h2 class="card-title">{{ pokemon.name }}</h2>
        <p class="card-text">ID: {{ pokemon.id }}</p>
        <h3 class="card-title">Movimientos:</h3>
        <ul>
            <li v-for="move in pokemon.moves.slice(0, 5)" :key="move.move.name">{{ move.move.name }}</li>
        </ul>
        <h3 class="card-title">Habilidades:</h3>
        <ul>
            <li v-for="ability in pokemon.abilities" :key="ability.ability.name">{{ ability.ability.name }}</li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    props: {
        pokemon: Object
    }
}
</script>

<style scoped>
.card {
    width: 300px;
    margin: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.card-img-top {
    width: 100%;
    height: 200px;
    object-fit: cover;
    border-radius: 10px 10px 0 0;
}

.card-body {
    padding: 20px;
}

.card-title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 10px;
}

.card-text {
    font-size: 18px;
    margin-bottom: 20px;
}
</style>
