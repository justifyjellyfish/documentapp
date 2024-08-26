<template>
    <div id="app">
      <h1>Items</h1>
      
  
      <form @submit.prevent="addItem">
        <input v-model="newItem.name" placeholder="Item name" required />
        <input v-model="newItem.description" placeholder="Item description" required />
        <button type="submit">Add Item</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        items: [], // ตัวแปรเก็บข้อมูลที่ได้รับจาก Express.js
        newItem: {
          name: '',
          description: ''
        } // ตัวแปรเก็บข้อมูลที่จะเพิ่ม
      };
    },
    created() {
      this.fetchItems();
    },
    methods: {
      fetchItems() {
        axios
          .get('http://localhost:5000/api/items')
          .then(response => {
            this.items = response.data;
          })
          .catch(error => {
            console.error('Error fetching items:', error);
          });
      },
      addItem() {
        axios
          .post('http://localhost:5000/api/items', this.newItem)
          .then(response => {
            this.items.push(response.data); // เพิ่มข้อมูลใหม่ในรายการที่แสดง
            this.newItem.name = '';
            this.newItem.description = '';
          })
          .catch(error => {
            console.error('Error adding item:', error);
          });
      }
    }
  };
  </script>
  