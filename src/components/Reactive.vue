<template>
<p>items in cart : {{ cart.itemcart }}</p>
<button @click="increment">addItems</button>
<button @click="decrement" >removeItem</button>
</template>
<script setup>
import {reactive} from 'vue'

const cart = reactive({
    // initially,the cart is empty
    itemcart : 0 
});

// function for add items in cart
function increment(){
    cart.itemcart++;
}
// function for remove items in cart
function decrement(){
    if(cart.itemcart>0){
        cart.itemcart--;
    }
    
}
</script>
<!-- A reactive function in Vue.js is a way to make data automatically update the user interface (UI)
  whenever that data changes. It makes things dynamic without you having to manually refresh or update
   the UI. -->

   <!-- why use it-
  - to keep your UI and data in sync effortlessly
  - Great for building dynamic, interactive applications. 
   -->