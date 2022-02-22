<template>
  <div>
    <label for="quantity">Nombre de livres : </label>
    <input id="quantity" type="number" v-model="produit.quantite" />
  </div>

  <div>
    <label for="prix">Prix : </label
    ><input id="prix" type="number" v-model="produit.prix" />
  </div>
  <h2>Prix total HT : {{ totalPrixHT }}€</h2>
  <h2>Prix total TTC : {{ totalPrixTTC }}€</h2>
  <h3>Modifications : {{ produit.nbrModifs }}</h3>
</template>

<script setup lang="ts">
import { computed, reactive, watch } from 'vue';

const produit = reactive({
  quantite: 3,
  prix: 10,
  nom: 'livre',
  nbrModifs: 0,
});

const totalPrixHT = computed(() => produit.quantite * produit.prix);
const totalPrixTTC = computed(() => produit.quantite * produit.prix * 1.2);

watch(
  () => [produit.quantite, produit.prix],
  (nouvelleVal, ancienneVal) => {
    console.log(nouvelleVal, ancienneVal);
    produit.nbrModifs++;
  }
);
</script>

<style></style>
