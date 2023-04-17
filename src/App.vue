<template>
  <div class="header">
    <HeaderComponent/>
  </div>
  <div class=" container select">selecttype</div>
  <div class="container p-5 bg-black mt-3">
     <main>
        <CardGridComponent :cards="cards">
        </CardGridComponent>
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import CardGridComponent from './components/CardGridComponent.vue';
import HeaderComponent from './components/headerComponent.vue';

export default {
  name: 'App',
  components: {
    CardGridComponent,
    HeaderComponent
},
  data() {
    return {
      cards: [],
    };
  },
  methods: {
    getCards() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0')
        .then((res) => {
          this.cards = res.data.data;
          console.log(res.data.data);
        })
    },
  },
  mounted() {
    this.getCards();
  },
}
</script>