<template>
 <div class="col-12">
    <div class="card">
      <img :src="card.image_url" :alt="card.name" />
      <h3>{{ card.name }}</h3>
      <p>Attribute: {{ card.attribute }}</p>
      <p>Level/Rank: {{ card.level }}</p>
      <p>Type: {{ card.type }}</p>
      <p>Race: {{ card.race }}</p>
      <p>Attack: {{ card.atk }}</p>
      <p>Defense: {{ card.def }}</p>
    </div>
  </div>
  </template>
  
  <script>
  export default {
    name: 'Card',
    props: {
    data: {
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
    padding: 1rem;
    text-align: center;
  }
  </style>