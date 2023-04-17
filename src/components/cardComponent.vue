<template>
    <div class="card">
      <h2>{{ data.name }}</h2>
      <img :src="data.card_images[0].image_url" alt="">
      <p>{{ data.desc }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Card',
    props: {
      data() {
        return { 
            type: Object,
            required: true,
        }
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