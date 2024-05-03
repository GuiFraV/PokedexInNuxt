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
    <input v-model="word" type="text" placeholder="Enter search term" />
    <button @click="addNew">Search</button>
</template>