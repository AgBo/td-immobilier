<template>
  <div id="app">
    <BienAVendre v-for="bien in biens" :key="bien.id" :titre="bien.titre" :type="bien.type" :contact="bien.contact" :prix="bien.prix"></BienAVendre>
  </div>
</template>

<script>
import axios from "axios";
import BienAVendre from "./components/BienAVendre";

export default {
  name: "app",
  components: {
    BienAVendre
  },

  data() {
    return {
      biens: []
    };
  },
  created() {
    axios.get("http://localhost:3000/biens").then(resultat => {
      this.biens = resultat.data;
    });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
