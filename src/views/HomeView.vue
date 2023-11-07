<script setup lang="ts">
import Header from '@/components/Header.vue';
import TextArea from '@/components/TextArea.vue';
import { type Ref, ref } from 'vue';
import Note from '@/components/Note.vue';


const notes: Ref<any[]> = ref([]);

function addNote(noteText: string) {
  const creationDate = new Date();
  notes.value.push({ text: noteText, date: creationDate });
}

</script>

<template>
  <Header></Header>
  <main>
    <TextArea @createNote="addNote"></TextArea>
  </main>
  <section>
    <article class="notes-box" v-for="note in notes">
      <Note :text="note.text" :date="note.date"></Note>
    </article>
  </section>
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
  gap: 2rem;
  border-radius: 10px;
}

.notes-box {
  background-color: lightgray;
}
</style>
