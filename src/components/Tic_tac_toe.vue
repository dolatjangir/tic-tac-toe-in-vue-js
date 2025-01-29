<template>
    <div class="flex flex-col items-center justify-center min-h-screen bg-gray-900 text-white">
      <h1 class="text-3xl font-bold mb-4">Tic-Tac-Toe</h1>
  
      
      <div class="grid grid-cols-3 gap-2">
        <button
          v-for="(cell, index) in board"
          :key="index"
          class="w-20 h-20 flex items-center justify-center text-4xl bg-gray-800 border border-gray-600 cursor-pointer transition-all hover:bg-gray-700"
          :class="{ 'cursor-not-allowed': cell }"
          @click="makeMove(index)"
        >
          {{ cell }}
        </button>
      </div>
  

      <p v-if="winner" class="text-xl mt-4">{{ winnerMessage }}</p>
  
      
      <button
        class="mt-4 px-4 py-2 bg-blue-600 text-white font-bold rounded-md hover:bg-blue-500 transition"
        @click="resetGame"
      >
        Restart Game
      </button>
    </div>
  </template>
  
  <script>
  import { ref, computed } from "vue";
  
  export default {
    setup() {
      const board = ref(Array(9).fill(""));
      const currentPlayer = ref("X");
      const winner = ref(null);
  
      
      const winPatterns = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8],
        [0, 3, 6], [1, 4, 7], [2, 5, 8], 
        [0, 4, 8], [2, 4, 6]             
      ];
  
      // Function to make a move
      const makeMove = (index) => {
        if (!board.value[index] && !winner.value) {
          board.value[index] = currentPlayer.value;
          checkWinner();
          currentPlayer.value = currentPlayer.value === "X" ? "O" : "X";
        }
      };
  
      // Function to check for a winner
      const checkWinner = () => {
        for (let pattern of winPatterns) {
          const [a, b, c] = pattern;
          if (board.value[a] && board.value[a] === board.value[b] && board.value[a] === board.value[c]) {
            winner.value = board.value[a];
            return;
          }
        }
        if (!board.value.includes("")) {
          winner.value = "Draw";
        }
      };
  
     
      const winnerMessage = computed(() => {
        if (winner.value === "Draw") return "It's a Draw!";
        if (winner.value) return `Winner: ${winner.value} `;
        return `Current Turn: ${currentPlayer.value}`;
      });
  
      
      const resetGame = () => {
        board.value = Array(9).fill("");
        currentPlayer.value = "X";
        winner.value = null;
      };
  
      return {
        board,
        currentPlayer,
        winner,
        makeMove,
        winnerMessage,
        resetGame,
      };
    },
  };
  </script>
  
  
      