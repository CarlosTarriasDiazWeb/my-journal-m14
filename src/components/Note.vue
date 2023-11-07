<script setup lang="ts">

const props = defineProps<{
    text: string,
    date: Date
}>()

</script>

<template>
    <h2>{{ props.text }}</h2>
    <h2>{{ props.date }}</h2>
</template>