<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <v-card color="basil">
    <v-card-title class="text-center justify-center py-6">
      <h1 class="font-weight-bold text-h2 text-basil">
        Cocktail Recipes
      </h1>
    </v-card-title>
  </v-card>
  <RouterView />

</template>

<style scoped>
.bg-basil {
  background-color: #FFFBE6 !important;
}

.text-basil {
  color: #356859 !important;
}
</style>
