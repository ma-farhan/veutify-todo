<template>


  <v-container class="bg-surface">
 
    <div class="d-flex flex-wrap justify-center ga-3">
      <v-chip>Home</v-chip>
      <v-chip>Archive</v-chip>
      <v-chip>About</v-chip>
    </div>
    
    <div>
      <p class="font-weight-bold">To Do List</p>
    </div>
 
    <v-card>
      <div>
        <v-list>
          <v-list-item v-for="(item, index) in items" :key="index">
  <div class="d-flex justify-space-between align-center w-100">
    <span>{{ item }}</span>
    
    <div>
      <v-chip color="blue" text-color="white" class="ma-1">Archive</v-chip>
      <v-chip color="red" text-color="white" class="ma-1" @click="deleteItem(index)">
        Delete
      </v-chip>
    </div>
  </div>
</v-list-item>

        </v-list>
 
 
        <v-divider></v-divider>
        <br><br><br>
 
 
        <v-text-field
          v-model="newText"
          label="Add new Item"
          @keyup.enter="addItem"
        ></v-text-field>
 
 
        <v-btn @click="addItem" block color="blue" text-color="white">
          Add
        </v-btn>
      </div>
    </v-card>
  </v-container>


 </template>
 
 
 <script setup>
 import { ref } from 'vue'
 
 
 const newText = ref('');

 const items = ref([]);
 
 
 const addItem = () => {
  if (newText.value.trim() !== '') {
    items.value.push(newText.value.trim());
    newText.value = '';
  }
 };
 
 
 const deleteItem = (index) => {
  items.value.splice(index, 1);
 };
 </script>
 
 
 <style scoped>
 .font-weight-bold {
  font-weight: 700;
 }

 </style>
 
 
 
 