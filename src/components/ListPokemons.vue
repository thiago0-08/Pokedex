
<script setup>
const pokemon = defineProps(["name", "url"])
 const idPokemon = (pokemon.url.split('/')[6])
 const imageUrl = "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"+ idPokemon+".svg"

</script>

<template>
    <div class="col-md-4">
        <div class="card mb-3">
            <img :src="imageUrl"  height="80" alt="..." class="card-img-top mt-3">
            <p class="text-center">{{ pokemon.name }}</p>            
        </div>
    </div>
</template>

<style>

</style>