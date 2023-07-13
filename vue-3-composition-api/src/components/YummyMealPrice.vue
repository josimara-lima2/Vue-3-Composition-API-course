<template>
    <span>
        {{ priceComputed }}
    </span>
</template>

<script setup>
import {computed, inject} from "vue"
const props = defineProps({
        price:Number
    },)
const currencySymbol =  inject('currency')
        const priceComputed = computed(() => `${currencySymbol.value}${props.price.toFixed(2)}`)


</script>

<style  scoped>

</style>