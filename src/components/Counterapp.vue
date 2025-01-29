<template>
    <div :class="theme">
      <h1>Counter: {{ count }}</h1>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
      <button @click="reset">Reset</button>
      <br /><br />
      <button @click="toggleTheme">Toggle Theme</button>
    </div>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  
  export default {
    setup() {
      const count = ref(0);
      const theme = ref('light');
  
      const increment = () => count.value++;
      const decrement = () => count.value--;
      const reset = () => (count.value = 0);
  
      const toggleTheme = () => {
        theme.value = theme.value === 'light' ? 'dark' : 'light';
      };
  
      return {
        count,
        theme,
        increment,
        decrement,
        reset,
        toggleTheme
      };
    }
  };
  </script>
  
  <style>
  .light {
    background-color: white;
    color: black;
  }
  
  .dark {
    background-color: black;
    color: white;
  }
  
  button {
    margin: 5px;
  }
  </style>
  