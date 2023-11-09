<script setup lang="ts">
import { emojiToIcons } from '@/utils';

const props = defineProps<{
    text: string,
    date: Date,
    emoji: string
}>()

</script>

<template>
    <div class="box-1">
        <component :is="emojiToIcons[props.emoji]"></component>
        <p>{{ props.text }}</p>
    </div>
    <div class="box-2">
        <p>{{ props.date }}</p>
    </div>
</template>

<style scoped>
.box-1 {
    display: flex;
    gap: 20px;
}
</style>