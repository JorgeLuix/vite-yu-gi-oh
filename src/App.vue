<template>
  <div class="header">
    <HeaderComponent/>
  </div>

  <div class="container d-flex justify-content-between pt-3">
  <select v-model="selectedtype" class="rounded">
    <option value="">All</option>
    <option v-for="type in alltypes" :key="type" :value= "type"> {{ type }} </option>
  </select>
  <div>
    <h5>Total Cards: {{ filteredCards.length }}</h5> 
    </div>

</div>

  <div class="container bg-dark p-5 mt-3">
     <main>
       <div class="loader d-flex justify-content-center align-items-center" v-if="isLoading">
          <i class="fa-solid fa-cog fa-spin"></i>
      </div>
        <CardGridComponent v-if="!isLoading" :cards="filteredCards">
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
    HeaderComponent,
    
},
  data() {
    return {
      cards: [],
      selectedtype:'',
      isLoading: true
    };
  },
  computed: {
  alltypes() {
    const type = new Set();//crea un nuovo oggetto Set vuoto, per tenere traccia degli archetipi.
    this.cards.forEach((card) => {
      if (card.type) {
        type.add(card.type);
      }
    });
    return Array.from(type);
  },
  filteredCards() {
    if (!this.selectedtype) {
      return this.cards;
    }
    return this.cards.filter((card) => card.type === this.selectedtype);
  },
},
  methods: {
    getCards() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0')
        .then((res) => {
          this.cards = res.data.data;
          console.log(res.data.data);
        })
        .finally(() => {
          this.isLoading = false; //isLoading e false quando i dati sono stati caricati
        });
    },
  },
  mounted() {
    this.getCards();
  },
}
</script>

<style lang="scss" scoped>
.loader {
  position: absolute;
  top: 0;
  left:0;
  bottom: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.5);
  color: black;
  font-size: 4rem;
}
</style>