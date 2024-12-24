<template>
    <div>
        <select @change="emit('update-filter', $event.target.value)" :value="props.filter">
            <option v-for="option in filterOptions" :key="option.value" :value="option.value">
                {{ option.label }}
            </option>
        </select>
    </div>
</template>

<script setup>
const props = defineProps({
    filter: {
        type: String,
        requared: true
    }
})

const emit = defineEmits(['update-filter'])

const filterOptions = [
    { value: 'all', label: 'Все задачи' },
    { value: 'active', label: 'Активные задачи' },
    { value: 'completed', label: 'Выполненные задачи' }
]

</script>

<style scoped></style>