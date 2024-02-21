<script setup>
import { ref } from "vue";
// -- donnée réactive pour la saisie du libellé
const libelle = ref("");
// -- les events émis par le composant
const emit = defineEmits(["addc"]);
// -- handler utile si on veut gérer le submit de cette manière
// <form @submit.prevent="handlerSubmit">
function handlerSubmit() {
    // en dehors du template il faut se souvenir que libelle
    // est un objet avec l'attribut value (créé par ref())
    emit("addc", libelle.value);
    libelle.value = "";
}
</script>
<template>
    <form @submit.prevent="$event => $emit('addc', libelle)">
        <label for="chose">Chose : </label>
        <input type="text" v-model="libelle" placeholder="chose?" />
        <input type="submit" value="valider" />
    </form>
</template> 
<style scoped></style>