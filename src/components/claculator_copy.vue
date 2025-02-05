<template>
  <div class="w-72 mx-auto mt-12 p-5 border rounded-lg bg-gray-200 shadow-lg">
    <div class="mb-4">
      <input
        type="text"
        :value="display"
        disabled
        class="w-full p-2 text-2xl text-right border rounded-md bg-white shadow-inner"
      />
    </div> 
    <div class="grid grid-cols-4 gap-2">
      <button
        v-for="button in buttons"
        :key="button"
        @click="handlebutton(button)"
        class="p-4 text-xl font-semibold border rounded-md bg-gray-300 hover:bg-gray-400 active:bg-gray-500 focus:outline-none"
      >
        {{ button }}
      </button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const display = ref("");
    const buttons = [
      "7", "8", "9", "/",
      "4", "5", "6", "*",
      "1", "2", "3", "-",
      "0", ".", "=", "+",
      "C",
    ];
    
    const handlebutton = (button) => {
      if (button === "=") {
        try {
          display.value = eval(display.value);
        } catch (error) {
          display.value = "error";
        }
      } else if (button === "C") {
        display.value = "";
      } else {
        display.value += button;
      }
    };
    
    return {
      handlebutton,
      display,
      buttons,
    };
  },
};
</script>
