<template>
 <div class="col-12 col-sm-6 col-md-4 col-lg-12">
    <div class="card">
      <img :src="card.card_images[0].image_url" />
      <h5>{{ card.name }}</h5>
      <p> {{ card.archetype }}</p>
      <p> {{ card.type }}</p>
      
      
    </div>
   
  </div>
  
  </template>
  
  <script>
  export default {
    name: 'Card',
    props: {
    card: {
      type: Object,
      required: true,
    },
  },
    }
  
  </script>
  
  <style lang="scss" scoped>
  .card {
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
    //padding: 1rem;
    text-align: center;
  }
  </style>