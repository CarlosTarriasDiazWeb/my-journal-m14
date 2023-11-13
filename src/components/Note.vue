<script setup lang="ts">
import type { NoteType } from '@/models/Note';
import { emojiToIcons } from '@/utils';

const props = defineProps<{
    note: NoteType
}>()

</script>

<template>
    <div class="box-1">
        <component :is="emojiToIcons[props.note.emoji]"></component>
        <p>{{ props.note.text }}</p>
    </div>
    <div class="box-2">
        <p>today at {{ props.note.date }} | user_1</p>
    </div>
</template>

<style scoped>
.box-1 {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 20px;
}

.box-1>svg {
    width: 120px;
    height: 120px;
}

.box-2 {
    width: fit-content;
    display: flex;
    align-self: flex-end;
}
</style>