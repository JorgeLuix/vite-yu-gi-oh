<template>
  <div>
    <CardGridComponent :cards="cards">
    </CardGridComponent>
  </div>
</template>

<script>
import axios from 'axios';
import CardGridComponent from './components/CardGridComponent.vue';

export default {
  name: 'App',
  components: {
    CardGridComponent,
  },
  data() {
    return {
      cards: [],
    };
  },
  mounted() {
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0')
      .then(response => {
        this.cards = response.data.data;
      })
  }
}
</script>