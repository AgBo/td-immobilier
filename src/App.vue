<template>
  <div id="app">
    <BienAVendre v-for="bien in biensAAfficher" :key="bien.id" :titre="bien.titre" :type="bien.type" :contact="bien.contact" :prix="bien.prix"></BienAVendre>
    <Label> Biens à vendre :
	<input type="checkbox" v-model="filtre" >
	</Label>
	</div>
</template>

<script>
import axios from "axios";
import BienAVendre from "./components/BienAVendre";
import { filter } from 'minimatch';

export default {
  name: "app",
  components: {
    BienAVendre
  },

  data() {
    return {
      biens: [],
      filtre: false
    };
  },
  computed: {
    biensAVendre(){
        return this.biens.filter(bien => bien.vendu===false);
	},
	biensAAfficher (){
	if (this.filtre===false) {
		return this.biens 
	}	else {
		return this.biensAVendre
	}
	}
  },
  created() {
    axios.get("http://localhost:3000/biens").then(resultat => {
      this.biens = resultat.data
    });
  },
  
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
