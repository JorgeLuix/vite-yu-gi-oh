<template>
  <div class="header">
    <HeaderComponent/>
  </div>
  <div class="container">
  <select v-model="selectedArchetype">
    <option value="">All</option>
    <option v-for="archetype in archetypes" :key="archetype" :value="archetype">{{ archetype }}</option>
  </select>
</div>
  <div class="container p-5 bg-black mt-3">
     <main>
        <CardGridComponent :cards="filteredCards">
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
      selectedArchetype:'',
    };
  },
  computed: {
  archetypes() {
    const archetypes = new Set();//crea un nuovo oggetto Set vuoto, per tenere traccia degli archetipi.
    this.cards.forEach((card) => {
      if (card.archetype) {
        archetypes.add(card.archetype);
      }
    });
    return Array.from(archetypes);
  },
  filteredCards() {
    if (!this.selectedArchetype) {
      return this.cards;
    }
    return this.cards.filter((card) => card.archetype === this.selectedArchetype);
  },
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