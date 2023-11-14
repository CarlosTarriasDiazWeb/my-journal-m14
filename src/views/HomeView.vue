<script setup lang="ts">
import Header from '@/components/Header.vue';
import TextArea from '@/components/TextArea.vue';
import { type Ref, ref, reactive } from 'vue';
import Note from '@/components/Note.vue';
import type { NoteType } from '../models/Note';

const notes = reactive<NoteType[]>([]);

function addNote(noteText: string, emoji: string) {
  const creationDate = new Date().toLocaleTimeString('en-US', {
    hour12: false,
    hour: "numeric",
    minute: "numeric"
  });
  notes.unshift({ id: window.crypto.randomUUID(), text: noteText, date: creationDate, emoji: emoji });
}
</script>

<template>
  <Header></Header>
  <main>
    <TextArea @createNote="addNote"></TextArea>
  </main>
  <section class="notes-box">
    <article class="note-box" v-for="note in notes" :key="note.id">
      <Note :note="note"></Note>
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
  width: 90%;
}

.note-box {
  background-color: lightgray;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 200px;
  padding: 15px;
  border-radius: 10px;
}
</style>
