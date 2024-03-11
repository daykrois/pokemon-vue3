<script setup>
import { onMounted, reactive } from 'vue';


onMounted(() => {
  getPokemonList();
})

function getPokemonList() {
  fetch("https://pokeapi.co/api/v2/pokemon?offset=0&limit=20")
    .then(response => response.json())
    .then(data => {
      data.results.forEach(pokemon => {
        pokemonList.push(pokemon)
      });
    })
}

function getPokemonName(){

}

const pokemonList = reactive([])


</script>

<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row justify="center">
          <v-col v-for="pokemon in pokemonList" cols="3">
            <v-card variant="tonal" >
              <v-card-item>
                <v-card-title>{{ pokemon.name }}</v-card-title>
              </v-card-item>
            </v-card>
          </v-col>

        </v-row>
      </v-container>
      <!-- <v-pagination v-model="page" :length="5" rounded="circle"></v-pagination> -->
    </v-main>
  </v-app>
</template>

<style scoped>
.v-app {
  background-color: rgb(178, 180, 184);
}


</style>
