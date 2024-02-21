<script setup>
import { reactive } from 'vue'
import Chose from "../Chose"
import ToDoListItem from "../components/ToDoListItem.vue"
import ToDoForm from './ToDoForm.vue';
const listeC = reactive([new Chose("menage"), new Chose("Vaiselle")]);
function handlerFaire(index) {
    listeC[index].faire();
}
function handlerDelete(index) {
    listeC.splice(index, 1);
}
function handlerAdd(libelle) {
  // -- il faut créer une nouvelle "chsoe" instance de la classe
  listeC.push(new Chose(libelle));
}
</script>
<template>
    <h3>Liste des choses à faire</h3>
    <ToDoForm @addc="handlerAdd"></ToDoForm>
    <ul>
        <ToDoListItem v-for="(chose, index) in listeC" :key="[chose.id]" :ch="chose" :idx="index" :handlerD="handlerDelete"
            :handlerF="handlerFaire">
        </ToDoListItem>
        <!-- <li v-for="(chose, index) in listeC" :key=[chose.id]>
            {{ chose.pourAfficher() }}
            <button @click="handlerDelete(index)">Delete</button>
            <button @click="handlerFaire(index)">Faire</button>
        </li> -->

    </ul>
</template>
<style scoped></style>