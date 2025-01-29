<template>
    <div class="app">
      <h1>Task Manager</h1>
  
      <!-- Task Input -->
      <input v-model="newTask" placeholder="Enter a task" @keyup.enter="addTask" />
      <button @click="addTask">Add Task</button>
  
      <!-- Task List -->
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          {{ task }}
          <button @click="removeTask(index)">Delete</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Reactive variables
  const tasks = ref([]); // Array to store tasks
  const newTask = ref(''); // Input for new task
  
  // Add a task to the list
  const addTask = () => {
    if (newTask.value.trim()) {
      tasks.value.push(newTask.value);
      newTask.value = ''; // Clear the input field
    }
  };
  
  // Remove a task by its index
  const removeTask = (index) => {
    tasks.value.splice(index, 1);
  };
  </script>
  
  <style scoped>
  .app {
    font-family: Arial, sans-serif;
    margin: 20px auto;
    width: 300px;
    text-align: center;
  }
  
  input {
    padding: 8px;
    width: 80%;
    margin-bottom: 10px;
  }
  
  button {
    margin-left: 5px;
    padding: 8px;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin: 5px 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  li button {
    background-color: red;
    color: white;
    border: none;
    padding: 4px 8px;
    cursor: pointer;
  }
  </style>
  