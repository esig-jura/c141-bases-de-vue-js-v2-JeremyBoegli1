<template>
  <v-container max-width="700">
    <!-- Données de l'exercice -->
    <exercice-objectifs number="8"/>
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <!-- Liste des Pokémon -->
      <v-card class="mx-auto my-6 pa-2" max-width="500">
        <v-card-title>Liste des Pokémon</v-card-title>
        <v-card-text>
          <v-list>
            <PokemonCard
              v-for="(pokemon, index) in pokemons"
              :key="index"
              :name="pokemon"
              :index="index"
              @remove="removePokemon"
            />
          </v-list>
        </v-card-text>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
import { ref } from "vue";
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";
import PokemonCard from "@/components/PokemonCard.vue";

// Liste initiale des Pokémon
const pokemons = ref(["Pikachu", "Bulbizarre", "Salamèche", "Carapuce", "Rondoudou"]);

// Supprimer un Pokémon de la liste
const removePokemon = (index) => {
  pokemons.value.splice(index, 1);
};
</script>

<style scoped>
/* Ajoute du style si nécessaire */
</style>
