<template>
    <div>
        <p v-show="timeLeft > 0">Осталось времени: {{ timeLeft }} секунд</p>
        <p v-show="timeLeft === 0">Время вышло</p>
        <button @click="resetTimer">Сбросить</button>
    </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
const timeLeft = ref(10)
let timerInterval = null

const startTimer = () => {
    stopTimer() // Очищаем предыдущией
    timerInterval = setInterval(() => {
        if (timeLeft.value > 0) {
            timeLeft.value--
        } else {
            stopTimer()
        }
    }, 1000)
}

const stopTimer = () => {
    if (timerInterval) {
        clearInterval(timerInterval)
        timerInterval = null
    }
}
const resetTimer = () => {
    timeLeft.value = 10
    startTimer()
}

onMounted(startTimer)
onUnmounted(stopTimer)

</script>

<style lang="scss" scoped></style>