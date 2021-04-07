<template>
    <div>
        <h3>API Pokemon</h3>
        <div v-for="(pokemon, index) in pokemons" :key="index" class="pokemon">{{pokemon.name}}</div>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            pokemons: []
        }
    },
    mounted: function() {
        this.$http
        .get('https://pokeapi.co/api/v2/pokemon?limit=20')
        .then((response) => {
            console.log(response.data.results);
            this.pokemons = response.data.results;
        })
    }
}
</script>

<style scoped>
    h3 {
        text-align: center;
    }
    .pokemon {
        text-align: center;
        color: red;
        padding: 5px 0;
    }
</style>