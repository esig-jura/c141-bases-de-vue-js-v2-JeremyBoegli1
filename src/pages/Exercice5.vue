<template>
  <v-container max-width="700">
    <!-- Donnée de l'exercice -->
    <exercice-objectifs number="5" />
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <v-card class="mx-auto my-6 pa-2" max-width="500">
        <v-card-title>Saisie surveillée</v-card-title>

        <v-card-text>
          <!-- 🚨 Affichage du message si "Pokémon" est détecté -->
          <v-alert v-if="containsPokemon" type="success" class="mb-2">
            Vous avez mentionné "Pokémon" !
          </v-alert>

          <!-- 👀 Champ de saisie surveillé -->
          <v-text-field
            v-model="userInput"
            label="Tapez quelque chose"
            placeholder="Essayez d'écrire Pokémon"
            outlined
          />

          <!-- 🔢 Affichage dynamique du nombre de caractères saisis -->
          <v-card-subtitle>
            Nombre de caractères : <strong>{{ characterCount }}</strong>
          </v-card-subtitle>
        </v-card-text>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
import { ref, computed, watch } from "vue";
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";

// 🔢 Variable réactive pour la saisie utilisateur
const userInput = ref("");

// 🚨 Variable réactive pour indiquer si "Pokémon" est présent
const containsPokemon = ref(false);

// 🔢 Calcul dynamique du nombre de caractères saisis
const characterCount = computed(() => userInput.value.length);

// 🔄 Définition de la limite de caractères
const MAX_LENGTH = 20;

// 👀 Watcher pour surveiller la saisie utilisateur
watch(userInput, (newValue) => {
  // Vérifier si le texte contient "Pokémon" (insensible à la casse)
  containsPokemon.value = /pokémon/i.test(newValue);

  // 🔄 Réinitialiser si le texte dépasse la limite
  if (newValue.length > MAX_LENGTH) {
    userInput.value = "";
  }
});
</script>
