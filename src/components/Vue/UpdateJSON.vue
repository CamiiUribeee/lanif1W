<script setup>
    import { ref } from 'vue'
    import data from '../data.json'

    let newFolder = ref("")

    function appendToJSON() {
    }

</script>

<template>
    <section class="max-w-6xl w-full mx-auto flex flex-col justify-start items-start">
        <h1>Ingrese la carpeta a agregar:</h1>
        <input type="text" v-model="newFolder" placeholder="Carpeta">
        <button @click="appendToJSON">Here</button>
    </section>
</template>