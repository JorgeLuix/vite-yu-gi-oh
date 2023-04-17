<template>
     <section class="card-grid">
        <cardComponent v-for="card in cards" :key="card.id" :card="card">
           
        </cardComponent>
    </section>
  </template>
  
  <script>

import cardComponent from './cardComponent.vue';
  
  export default {
    name: 'CardGrid',
    components: { cardComponent },
    props: {
        cards: Object,
        required: true
    }
  }
  </script>
  
  <style lang="scss" scoped>
   .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-gap: 1rem;
   }
  </style>