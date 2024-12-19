<template>
    <div>
        <h2>Создал компонент</h2>
        <p>Админ {{ userName }}</p>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const userName = ref('Dima')
</script>

<style scoped>
h2 {
    color: blue;
}
</style>