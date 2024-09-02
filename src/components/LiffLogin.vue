<template>
    <v-container>
      <v-btn @click="loginWithLINE">Login with LINE</v-btn>
    </v-container>
  </template>
  
  <script>
  import liff from '@line/liff';
  
  export default {
    name: 'LiffLogin',
    methods: {
      async loginWithLINE() {
        try {
          await liff.init({ liffId: '2005937488-5q2Kd2lk' });
          if (!liff.isLoggedIn()) {
            liff.login();
          }
        } catch (error) {
          console.error('Error initializing LIFF:', error);
        }
      }
    }
  }
  </script>