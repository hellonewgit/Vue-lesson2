<template>
    <div>
        <input type="text" @keyup.enter="addTodo" v-model="newTodo">
        <button @click="addTodo">Добавить</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
const emit = defineEmits(['add-todo'])
const newTodo = ref('')

const addTodo = () => {
    if (newTodo.value.trim()) {
        emit('add-todo', newTodo.value.trim())
        newTodo.value = ''
    }
}

</script>

<style scoped></style>