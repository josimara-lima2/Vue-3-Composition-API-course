<template>
    <div>
        <p>
            <strong>{{ name }}</strong>

            <YummyMealPrice :price="price"></YummyMealPrice>
        </p>
        <button @click="addToCart">add to cart</button>
    </div>
</template>

<script setup>
    import {  computed } from 'vue';
import YummyMealPrice from './YummyMealPrice.vue';
const props = defineProps({
            name: String, 
            price:Number
        })

    const emit = defineEmits(['addToCart'])
const addToCart = () => emit('addToCart', props.name)
 
</script>

<style scoped>

</style>