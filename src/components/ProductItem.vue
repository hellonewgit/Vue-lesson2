<template>
    <div class="product">
        <h3>{{ product.name }}</h3>
        <p>{{ product.desc }}</p>
        <p>{{ product.price }} руб.</p>
        <p>Общая сумма {{ totalPrice }} руб.</p>
        <Counter @update="updateQuantity" />
        <button>Купить</button>
    </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import Counter from './shop/Counter.vue';
const props = defineProps({
    product: Object
})
const quantity = ref(0)
const totalPrice = computed(() => props.product.price * quantity.value)

const updateQuantity = (change) => {
    quantity.value += change
}




</script>

<style scoped>
.product {
    border: 1px solid black;
    padding: 8px 24px 24px;
    border-radius: 24px;
}
</style>