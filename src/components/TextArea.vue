<script setup lang="ts">
import { type Ref, ref, computed, watch } from 'vue';
import Happy from './icons/Happy.vue';

const text: Ref<string> = ref("");

const emit = defineEmits<{
    createNote: [text: string]
}>()

const textLength = computed<number>((): number => {

    if (text.value.length <= 280) {
        return text.value.length
    }
    else {
        return 280;
    }

})

watch(text, () => {
    if (text.value.length >= 280) {
        text.value = text.value.substring(0, 280);
    }
})

function postNote() {
    emit('createNote', text.value);
}

</script>

<template>
    <form @submit.prevent="postNote()">
        <textarea v-model.trim="text" name="journal" id="journal"></textarea>
        <div>
            <Happy></Happy>
        </div>
        <div>
            <span>{{ textLength }} / 280</span>
            <button type="submit">Recordar</button>
        </div>
    </form>
</template>
<style scoped>
form {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 2rem;
    justify-content: flex-start;
}

textarea {
    border: none;
    overflow: auto;
    outline: none;

    -webkit-box-shadow: none;
    -moz-box-shadow: none;
    box-shadow: none;

    resize: none;
    /*remove the resize handle on the bottom right*/
}

textarea {
    width: 95%;
    resize: none;
    border-radius: 10px;
    padding: 20px;
}
</style>
