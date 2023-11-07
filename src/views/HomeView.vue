<script setup lang="ts">
import Header from '@/components/Header.vue';
import TextArea from '@/components/TextArea.vue';
</script>

<template>
  <Header></Header>
  <main>
    <TextArea></TextArea>
    <div>Hola</div>
  </main>
</template>
<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  background-color: lightgray;
  padding: 2rem;
  width: 45%;
  gap: 1rem;
  border-radius: 10px;
}
</style>
