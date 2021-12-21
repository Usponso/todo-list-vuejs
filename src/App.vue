<template>
  <div id="app">
    <label>
      Nom de la tâche
    </label>
    <input type="text" name="new-tache" v-model="nomTache" />
    <ajouterBouton class="btnAjouter" @ajouterTache="ajouter"/>

    <h2>Tâches :</h2>
    <ul>
      <li v-for="(tache, index) in taches" :key="tache.name"><input type="checkbox" v-model="tache.checked"/> 
      <div :class="{termine: tache.checked}">{{ tache.name }}</div>
      <button @click="supprimer(index)" class="btnSupprimer">Supprimer</button></li>
    </ul>
  </div>
</template>

<script>
import ajouterBouton from "./components/AjouterBouton.vue"

export default {
  name: 'App',
  data() {
    return {
      check: "",
      nomTache: "",
      newTache: {name: "", checked: ""},
      taches: []
    }
  },
  components: {
    ajouterBouton,
  },
  methods: {
    ajouter(){
      this.taches.push({name: this.nomTache, checked: ""})
    },
    supprimer(index){
      this.taches.splice(index,1)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
input[type="text"]{
  padding: 7px;
  border-radius: 5px;
  border: 1px solid darkgrey;
}
ul{
  list-style: none;
}
li{
  display: flex;
  place-content: space-evenly;
  padding: 5px;
}
.termine{
  color: grey;
  text-decoration: line-through;
  text-decoration-color: red;
  font-style: italic;
}
.btnAjouter{
  padding: 10px;
  background-color: green;
  color: white;
  border-radius: 4px;
  border: none;
  cursor: pointer;
}
.btnSupprimer{
  padding: 10px;
  background-color: red;
  color: white;
  border-radius: 4px;
  border: none;
  cursor: pointer;
}
</style>
