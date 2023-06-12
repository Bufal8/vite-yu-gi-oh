<script>
import { store } from "./store.js";
import axios from "axios";
import AppHeader from './components/AppHeader.vue';
import DropDown from './components/DropDown.vue';
import CardList from './components/CardList.vue';



export default {
  components: {
    AppHeader,
    DropDown,
    CardList
  },
  data() {
    return {
      store,
    }
  },
  methods: {
    getCards() {
      let myUrl = store.apiURL;

      if (store.archSelect !== "") {
        myUrl += `?archetype=${store.archSelect}` //Filter based on selected Archetype
      } else {
        myUrl += "?num=20&offset=0" //Filter just 20 elements
      }
      axios.get(myUrl)
        .then(res => {
          store.cardList = res.data.data
          console.log(store.cardList);
        })
        .catch(err => {
          console.log(err);
        })
    },
    archetypeList() {
      axios.get(store.apiArchURL)
        .then(res => {
          store.archList = res.data
          console.log(store.archList);
        })
    }
  },
  created() {
    this.getCards();
    this.archetypeList();
  }

}
</script>

<template>
  <AppHeader message="Yu-Gi-Oh Api" />

  <!-- Dropdown section -->
  <div class="container">
    <DropDown @archSelected="getCards" />
  </div>

  <!-- Cards section -->
  <CardList />
</template>

<style lang="scss">
@use './styles/general.scss';
</style>