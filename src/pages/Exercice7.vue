<template>
  <v-container max-width="700">
    <!-- Données de l'exercice -->
    <exercice-objectifs number="7"/>
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <v-card
        class="mx-auto my-6 pa-2"
        max-width="500"
      >
        <v-card-title>
          Coucou
        </v-card-title>
        <v-card-text>
          <p>Je suis là !</p>
        </v-card-text>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
import { onMounted, onUnmounted } from "vue";
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";

// Affichage de l'alerte au montage du composant
onMounted(() => {
  alert("Composant monté avec succès !");
});

// Affichage de l'alerte au démontage du composant
onUnmounted(() => {
  alert("Composant démonté !");
});
</script>

<style scoped lang="sass">
</style>
