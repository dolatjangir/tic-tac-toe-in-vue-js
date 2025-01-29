<template>
    <div class="notes-app">
      <h1>Notes App</h1>
      <input
        v-model="newNote"
        placeholder="Write a new note..."
        @keyup.enter="addNote"
      />
      <button @click="addNote">Add Note</button>
      <ul>
        <li v-for="(note, index) in notes" :key="index">
          <p>{{ note }}</p>
          <button @click="deleteNote(index)">Delete</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      // Reactive state for notes
      const notes = ref([]);
      const newNote = ref('');
  
      // Method to add a new note
      const addNote = () => {
        if (newNote.value.trim()) {
          notes.value.push(newNote.value.trim());
          newNote.value = ''; // Clear input after adding
        }
      };
  
      // Method to delete a note
      const deleteNote = (index) => {
        notes.value.splice(index, 1); // Remove the note at the given index
      };
  
      // Expose variables and methods to the template
      return {
        notes,
        newNote,
        addNote,
        deleteNote
      };
    }
  };
  </script>
  
  <style>
  .notes-app {
    font-family: Arial, sans-serif;
    margin: 20px auto;
    width: 400px;
    text-align: center;
  }
  
  input {
    width: 80%;
    padding: 8px;
    margin-bottom: 10px;
  }
  
  button {
    margin-left: 5px;
    padding: 5px 10px;
    cursor: pointer;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    background: #f9f9f9;
    margin: 5px 0;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  
  button {
    background-color: #ff6666;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #ff4d4d;
  }
  </style>
  