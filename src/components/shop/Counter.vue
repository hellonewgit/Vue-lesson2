<template>
    <div>
        <div class="count">
            <button :disabled="count <= 1" @click="downCount" class="count__minus">-</button>
            <p class="count__show">{{ count }}</p>
            <button @click="upCount" class="count__plus">+</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
const count = ref(0)

const emit = defineEmits(['update'])

const upCount = () => {
    count.value++
    emit('update', 1)
}

const downCount = () => {
    if (count.value > 0) {
        count.value--
        emit('update', -1)
    }
}

</script>

<style lang="sass" scoped>
.count 
    display: flex  
    align-items: center
    gap: 16px

    &__show
        font-weight: bold
        color: black
    

.heading 
    text-decoration: underline



</style>