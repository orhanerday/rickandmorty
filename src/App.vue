<template>
  <div id="app">
    <img height="250" alt="Vue logo" src="./assets/logo.png" />
    <div class="cards-list">
      <Card 
      v-for="character in characters"
      :key="character.id"
      :c-info="character"
      
      />
    </div>
  </div>
</template>

<script>
import Card from "./components/Card.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    Card,
  },
  data(){
    return{
      characters: null
    }
  },
  mounted() {
    axios
      .get("https://rickandmortyapi.com/api/character")
      .then((response) => {
        this.characters = response.data.results;
        
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
  
};
</script>
<style>
#app {

  text-align: center;

}
</style>
