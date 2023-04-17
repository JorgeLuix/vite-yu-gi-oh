<template>
     <section class="container ">
        <div class="row">
          <cardComponent v-for="card in cards" :key="card.id" :card="card"
          class="col-12 col-md-6 col-lg-3 mb-4">
          </cardComponent>
       </div>
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
   
   
  </style>