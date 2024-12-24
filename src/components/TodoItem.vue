<template>
    <div>
        <div>
            <input type="checkbox" @change="$emit('toggle')" :checked="todo.complited">
            <span :class="{ 'complited': todo.complited }">{{ todo.text }}</span>
            <button @click="$emit('delete')">X</button>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    todo: {
        type: Object,
        required: true
    }
})

const emit = defineEmits(['toggle', 'delete'])

</script>

<style scoped>
.complited {
    text-decoration: line-through;
}
</style>