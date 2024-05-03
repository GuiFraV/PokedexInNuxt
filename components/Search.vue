<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const word = ref('');
const router = useRouter();
const loading = ref(false); 

const addNew = async () => {
    if (word.value !== "") {
        loading.value = true; 
        try {
            const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${word.value.toLowerCase()}`);
            if (response.ok) {
                router.push(`/${word.value.toLowerCase()}`);
            } else {
                router.push('/error');
            }
        } catch (error) {
            router.push('/error');
        } finally {
            loading.value = false;
        }
    }
}
</script>

<template>
    <header>
        <input v-model="word" @keyup.enter="addNew" type="text" placeholder="Enter search" />
        <button class="search" @click="addNew">Search</button>
        <div class="loading" v-if="loading">Loading...</div> 
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

.loading{
    color:white
}

</style>