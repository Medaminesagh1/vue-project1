<script setup>
defineProps(["ch","idx","handlerD","handlerF"]);
</script>
<template>
    <li>
        {{ ch.pourAfficher() }}
        <button @click="()=>handlerD(idx)">Delete</button>
        <button @click="()=>handlerF(idx)">Faire</button>
    </li>
</template>
<style scoped></style>