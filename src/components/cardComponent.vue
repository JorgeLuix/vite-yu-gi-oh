<template>
 <div class="col-12 col-sm-6 col-md-4 col-lg-3">
    <div class="card">
      <img :src="card.card_images[0].image_url" />
      <div class="pt-3">
      <h5>{{ card.name }}</h5>
       <div class="d-flex justify-content-around">
        <p class="text-muted"> {{ card.archetype }}</p>
        <p class="text-muted"> {{ card.type }}</p>
      </div>
    </div>
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
    background-color: #c7c5c5;
    border-radius: 8px;
    box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
    padding: 1rem;
    text-align: center;
    width: 100%;
  }
  .card-title{
    overflow: hidden;
    text-overflow: ellipsis;
  }
  </style>