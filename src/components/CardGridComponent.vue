<template>
     <div class="card-grid">
    <cardComponent v-for="card in cards" :key="card.id" :data="card"></cardComponent>
  </div>
  </template>
  
  <script>

import cardComponent from './cardComponent.vue';
  
  export default {
    name: 'CardGrid',
    components: {
    cardComponent,
    
},
    props: {
      cards: {
        type: Array,
        required: true,
      },
    },
  }
  </script>
  
  <style lang="scss" scoped>
 
  </style>