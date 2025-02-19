<template>
  <v-container max-width="700">
    <!-- Donnée de l'exercice -->
    <exercice-objectifs number="4" />
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <v-card class="mx-auto my-6 pa-2" max-width="500">
        <v-card-title>Saisie avec limite de caractères</v-card-title>

        <!-- 🧮 Affichage dynamique du nombre de caractères restants -->
        <v-card-subtitle>
          Caractères restants :
          <strong>{{ remainingCharacters }}</strong>
        </v-card-subtitle>

        <v-card-text>
          <!-- ⚠️ Avertissement si la limite est dépassée -->
          <v-alert v-if="remainingCharacters < 0" type="error" class="mb-2">
            Vous avez atteint la limite maximale de caractères !
          </v-alert>

          <!-- 🔗 Liaison du champ de texte avec v-model -->
          <v-text-field
            ref="textField"
            v-model="userInput"
            outlined
            rows="2"
            label="Tapez votre texte ici"
            :counter="MAX_LENGTH"
          />
        </v-card-text>

        <v-card-actions>
          <!-- 🎯 Bouton pour activer le focus sur le champ de texte -->
          <v-btn color="primary" @click="focusTextField">
            Activer le champ de texte
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
import { ref, computed } from "vue";
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";

// Constante pour la limite de caractères
const MAX_LENGTH = 20;

// 🔗 Variable réactive pour stocker le texte saisi
const userInput = ref("");

// 🧮 Propriété calculée pour le nombre de caractères restants
const remainingCharacters = computed(() => MAX_LENGTH - userInput.value.length);

// 🎯 Référence pour le champ de texte et fonction pour appliquer le focus
const textField = ref(null);
const focusTextField = () => {
  textField.value?.focus();
};
</script>
