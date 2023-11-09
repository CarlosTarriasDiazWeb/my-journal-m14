<script setup lang="ts">
import { type Ref, ref, computed, watch } from 'vue';
import { emojiToIcons } from '@/utils';

const text: Ref<string> = ref("");

const emit = defineEmits<{
    createNote: [text: string, emoji: string],
    setEmoji: [emoji: string]
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
    if (text.value.length > 0 && currentEmoji.value !== "") {
        emit('createNote', text.value, currentEmoji.value);
        text.value = "";
    }
}

const currentEmoji: Ref<string> = ref("");

const emojis: Ref<string[]> = ref(["Happy", "Sad", "Surprised"]);

function setEmoji(emoji: string) {
    currentEmoji.value = emoji;
}


</script>

<template>
    <form @submit.prevent="postNote()">
        <textarea v-model.trim="text" name="journal" id="journal"></textarea>
        <section class="icon-container">
            <span :class="{ active: emoji === currentEmoji }" @click="setEmoji(emoji)" v-for="(emoji, index) in emojis ">
                <component :is="emojiToIcons[emoji]"></component>
            </span>
        </section>
        <div class="button-container">
            <div class="text-length">
                <span>{{ textLength }} / 280</span>
            </div>
            <div class="submit-btn">
                <button type="submit">Recordar</button>
            </div>

        </div>
    </form>
</template>
<style scoped>
.button-container {
    display: flex;
    flex-direction: row;
    width: 100%;
    gap: 1rem;
}

button {
    background-color: rgb(12, 98, 22);
    color: white;
    padding: 5px;
    width: 80px;
    height: 40px;
    border-radius: 5px;
    cursor: pointer;
}

.text-length {
    flex-grow: 0.5;
}

.submit-btn {
    align-self: flex-end;
}

.button-container .text-length {
    text-align: left;
}

.icon-container {
    display: flex;
    flex-direction: row;
    gap: 2px;
}

span {
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.active {
    background-color: lightblue;
}

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
