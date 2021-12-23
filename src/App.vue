<template>
  <div id="app">

    <TodoListLayout>
      <template #header="{ appName }">
        <h1>{{ appName }}</h1>
      </template>

      <template #main>
        <label>
          Nom de la tâche
        </label>
        <input type="text" name="new-tache" v-model="nomTache" @keydown.enter="ajouter" />
        <AjouterBouton class="btnAjouter" @ajouterTache="ajouter">
          Ajouter
        </AjouterBouton>

        <h2>Tâches :</h2>
        <ul>
          <li v-for="(tache, index) in taches" :key="tache.name">
            <input type="checkbox" v-model="tache.checked"/> 
            <div :class="{termine: tache.checked}">{{ tache.name }}</div>
            <button @click="supprimer(index)" class="btnSupprimer">Supprimer</button>
          </li>
        </ul>
      </template>

      <template #footer>
        <CustomInput label="Mon label custom" v-model="maData" ></CustomInput>
        Voici maData : {{ maData }}<br/>

        Ceci est le footer
      </template>
    </TodoListLayout>

  </div>
</template>

<script>
import TodoListLayout from "./components/TodoListLayout.vue" 
import AjouterBouton from "./components/AjouterBouton.vue"
import CustomInput from "./components/CustomInput.vue"

export default {
  name: 'App',
  data() {
    return {
      check: "",
      nomTache: "",
      newTache: {name: "", checked: ""},
      taches: [],
      maData: "valeur par défaut",
    }
  },
  components: {
    TodoListLayout,
    AjouterBouton,
    CustomInput,
  },
  methods: {
    ajouter(){
      this.taches.push({name: this.nomTache, checked: ""})
      this.nomTache = ""
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
