<template>
    <div>
        <h1>Список задач</h1>
        <TodoFilter :filter="filter" @update-filter="updateFilter" />
        <TodoInput @add-todo="addTodo" />
        <TodoList :todos="filteredTodos" @delete-todo="deleteTodo" @toggle-todo="toggleTodo" />
    </div>
</template>

<script setup>
import { computed, ref } from 'vue';
import TodoFilter from './TodoFilter.vue';
import TodoInput from './TodoInput.vue';
import TodoList from './TodoList.vue';

const todos = ref([]);
const filter = ref('all');

const filteredTodos = computed(() => {
    switch (filter.value) {
        case 'active':
            return todos.value.filter(todo => !todo.complited);
        case 'completed':
            return todos.value.filter(todo => todo.complited);
        default:
            return todos.value;
    }
})

const addTodo = (text) => {
    todos.value.push({
        id: Date.now(),
        text,
        complited: false
    })
}

const deleteTodo = (id) => {
    todos.value = todos.value.filter(todo => todo.id !== id);
}

const toggleTodo = (id) => {
    const todo = todos.value.find(todo => todo.id === id);
    if (todo) {
        todo.complited = !todo.complited;
    }
}

const updateFilter = (newFilter) => {
    filter.value = newFilter;
}
</script>

<style scoped></style>