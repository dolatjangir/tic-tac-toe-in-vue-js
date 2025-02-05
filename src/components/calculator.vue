<template>
    <div class="calculator">
      <div class="calculator-screen">
        <input
          type="text"
          :value="display"
          disabled
          class="screen"
        />
      </div>
      <div class="calculator-buttons">
        <button v-for="button in buttons" :key="button" @click="handleClick(button)" class="button">
          {{ button }}
        </button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from "vue";
  
  export default {
    setup() {
      // Reactive variable to hold the screen value
      const display = ref("");
      
      // Buttons for calculator layout
      const buttons = [
        "7", "8", "9", "/",
        "4", "5", "6", "*",
        "1", "2", "3", "-",
        "0", ".", "=", "+",
        "C",
      ];
  
      // Handle button clicks
      const handleClick = (button) => {
        if (button === "=") {
          // Evaluate the expression when "=" is clicked
          try {
            display.value = eval(display.value);
          } catch (error) {
            display.value = "Error";
          }
        } else if (button === "C") {
          // Clear the screen when "C" is clicked
          display.value = "";
        } else {
          // Append the clicked button to the display
          display.value += button;
        }
      };
  
      return {
        display,
        buttons,
        handleClick,
      };
    },
  };
  </script>
  
  <style>
  .calculator {
    width: 300px;
    margin: 50px auto;
    border: 1px solid #ccc;
    border-radius: 10px;
    padding: 20px;
    background-color: #f0f0f0;
  }
  
  .calculator-screen {
    margin-bottom: 20px;
  }
  
  .screen {
    width: 100%;
    padding: 10px;
    font-size: 2rem;
    text-align: right;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #fff;
  }
  
  .calculator-buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  
  .button {
    padding: 20px;
    font-size: 1.5rem;
    border: none;
    background-color: #eee;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .button:hover {
    background-color: #ddd;
  }
  
  .button:active {
    background-color: #ccc;
  }
  </style>
  