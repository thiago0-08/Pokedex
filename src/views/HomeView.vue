<script setup>
import { onMounted, reactive, ref} from 'vue';
import ListPokemons from '../components/ListPokemons.vue';

let pokemons = reactive(ref());

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=20")
  .then(response => response.json())
  .then(response => {
    pokemons.value = response.results
    console.log(pokemons)
  })
})
</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6" >
          <div class="card p-3" style="width: 100%;">
            <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/25.svg" height="300px" class="car-img-top" alt="">
            <div class="card-body">
              <h5 class="card-title">Pikachu</h5>
              <p class="card-text">Um resumo sobre um pokemom</p>
            </div>
          </div>
        </div>

        <div class="col-sm-12 col-md-6" >
          <div class="card" style="width: 100%;">
            <div class="card-body row">
              <listPokemons 
            v-for="pokemon in pokemons"
            :key="pokemon.name"
            :name="pokemon.name"
            :url="pokemon.url"
            />
            </div>
          </div>       
        </div>
      </div>
    </div>
  </main>
</template>