<template>
    <div>
        <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @delete="$emit('delete-todo', todo.id)"
            @toggle="$emit('toggle-todo', todo.id)" />
    </div>
</template>

<script setup>
import TodoItem from './TodoItem.vue';

const props = defineProps({
    todos: Array,
    requared: true
})

const emit = defineEmits(['delete-todo, toggle-todo'])


</script>

<style scoped></style>