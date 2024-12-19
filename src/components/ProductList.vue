<template>
    <div class="product-list">
        <h1>Каталог товаров</h1>
        <div class="product-list__items">
            <div v-for="product in products" :key="product.id" class="product-list__item">
                <ProductItem :product="product" />
            </div>
        </div>
    </div>
</template>

<script setup>
import ProductItem from './ProductItem.vue'
import { ref } from 'vue'
const products = ref([
    { id: 1, name: 'Ноутбук', price: 1000, desc: 'Описание товара номер 1' },
    { id: 2, name: 'Телефон', price: 500, desc: 'Описание товара номер 2' },
    { id: 3, name: 'Компьютер', price: 2000, desc: 'Описание товара номер 3' },
])

</script>

<style scoped>
.product-list__items {
    display: flex;
    flex-wrap: wrap;
    gap: 24px;
    text-align: left;
}
</style>