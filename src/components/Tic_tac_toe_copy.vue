<template>
    <div class="flex flex-col items-center justify-center min-h-screen bg-gray-900 text-white">
        <h1 class="text-3xl font-bold mb-4">Tic-Tac-Toe</h1>
         <!-- Game Board -->
      <div class="grid grid-cols-3 gap-2">
        <button
          v-for="(cell, index) in board"
          :key="index"
          class="w-20 h-20 flex items-center justify-center text-4xl bg-gray-800 border border-gray-600 cursor-pointer transition-all hover:bg-gray-700"
        
        >
          {{ cell }}
        </button>
      </div>
      </div>
</template>
<script>
 import { ref, computed } from "vue";
export default{
    setup(){
        const board = ref(Array(9).fill(""));
        const player = ref('X')
        return(
            board
        )
    }
}
</script>