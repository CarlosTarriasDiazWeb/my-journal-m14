<script setup lang="ts">
import Journal from "./icons/Journal.vue";
</script>

<template>
    <header>
        <Journal></Journal>
        <h1>My Journal</h1>
    </header>
</template>
<style scoped>
header {
    display: flex;
    justify-content: flex-start;
    gap: 1rem;
    width: 42%;
}
</style>
