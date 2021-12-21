<template>
    <button @click="emitAjouter">Ajouter</button>
</template>

<script>
export default{
    name: "AjouterBouton",
    methods: {
        emitAjouter(){
            this.$emit("ajouterTache")
        }
    }
}

</script>

<style>

</style>