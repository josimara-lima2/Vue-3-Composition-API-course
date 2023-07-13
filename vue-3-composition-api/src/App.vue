<script setup>
import { provide, ref, watch } from 'vue';
import YummyMeal from './components/YummyMeal.vue';

const name = ref('Este é o nome')

   const placeOrder = () => {
      alert('Este é o alerta funcionando')
    }

    const cart = ref([])

    const addItemToCart = (item) => cart.value.push(item)
   
   /*  watch(name, (value, oldValue) => {
      console.log(value, oldValue)
    }) */

   const currencySymbol = ref('$')
    const removeWatch =  watch(() => [...cart.value], (v,oldV) => console.log(v, oldV))
    const meals = ref([
      {name:"coxinha 1", price:1},
      {name:"coxinha 2", price:2},
      {name:"coxinha 3", price:3},
      {name:"coxinha 4", price:4},
      {name:"coxinha 5", price:5},
      {name:"coxinha 6", price:6}
    ])

    provide('currency', currencySymbol)

</script>

<template>
  <div class="container">
    <input v-model="name"/>
    <button @click="placeOrder">Order</button>
    <button @click="removeWatch">removeWatch</button>
    <YummyMeal :key="index" v-for="(meal, index) in meals" :name="meal.name" :price="meal.price" @addToCart="addItemToCart" />
    <br>
    <label for="currencySymbol">currencySymbol</label>
    <select id="currencySymbol" v-model="currencySymbol">
    <option value="$">Dolar</option>
    <option value="R$">Real</option>
    </select>
  </div>
</template>

<style scoped>
.container{
  display: flex;
  flex-direction: column;
  gap: 2rem;
  width: 100%;
 justify-content: center;
 
 color: white;
  
}
</style>
