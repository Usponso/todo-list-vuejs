<template>
    <button @click="emitAjouter">
        <slot>Action</slot>
    </button>
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