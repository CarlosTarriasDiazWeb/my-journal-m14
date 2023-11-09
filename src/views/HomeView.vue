<script setup lang="ts">
import Header from '@/components/Header.vue';
import TextArea from '@/components/TextArea.vue';
import { type Ref, ref } from 'vue';
import Note from '@/components/Note.vue';
import type { NoteType } from '../models/Note';

const notes: Ref<NoteType[]> = ref([]);

function addNote(noteText: string, emoji: string) {
  const creationDate = new Date();
  notes.value.unshift({ id: Math.random(), text: noteText, date: creationDate, emoji: emoji });
}
</script>

<template>
  <Header></Header>
  <main>
    <TextArea @createNote="addNote"></TextArea>
  </main>
  <section class="notes-box">
    <article class="note-box" v-for="note in notes" :key="note.id">
      <Note :text="note.text" :date="note.date" :emoji="note.emoji"></Note>
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
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.note-box {
  background-color: lightgray;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 200px;
  padding: 10px;
  border-radius: 10px;
}
</style>
