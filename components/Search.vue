<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const word = ref('');
const router = useRouter();

const addNew = () => {
    if (word.value !== "") {
        router.push(`/${word.value}`);
    }
}
</script>

<template>
    <header>
        <input v-model="word" type="text" placeholder="Enter search" />
        <button class="search" @click="addNew">Search</button>
    </header>
</template>

<style>

header {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px;
}
input {
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
    width: 300px;
}

    .search {
        padding: 10px;
        margin: 10px;
        border-radius: 5px;
        border: 1px solid #ccc;
        background-color: #333;
        color: white;
        cursor: pointer;
    }

    .search:hover {
        background-color: #444;
    }

</style>