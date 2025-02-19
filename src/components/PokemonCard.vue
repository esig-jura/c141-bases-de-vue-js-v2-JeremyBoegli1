<template>
  <v-list-item>
    <v-list-item-title>
      *** {{ name }} ***
    </v-list-item-title>

    <template v-slot:append>
      <v-btn
        icon="mdi-delete"
        variant="text"
        @click="deletePokemon"
      ></v-btn>
    </template>
  </v-list-item>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

// Déclaration des props
const props = defineProps({
  name: String, // Reçoit le nom du Pokémon
  index: Number, // Reçoit l'index du Pokémon dans la liste
});

// Définition des événements
const emit = defineEmits(["remove"]);

// Méthode pour supprimer un Pokémon
const deletePokemon = () => {
  emit("remove", props.index); // Émet l'événement avec l'index
};
</script>

<style scoped>
/* Ajoute du style personnalisé si nécessaire */
</style>
