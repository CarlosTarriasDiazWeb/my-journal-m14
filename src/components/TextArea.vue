<script setup lang="ts">

</script>

<template>
    <form>
        <textarea name="journal" id="journal" cols="30" rows="10"></textarea>
    </form>
</template>
<style scoped>
form {
    width: 100%;
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
