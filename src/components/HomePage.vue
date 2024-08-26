<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
</script>

<template>
    <v-container fluid class="pa-0 fill-height">
      <v-row align="center" justify="center">
        <v-col cols="12" sm="8" md="6" lg="4">
          <v-card class="text-center pa-6" flat>
            <h1 class="text-h2 font-weight-bold green--text text--lighten-3 mb-6">Document Tracker</h1>
            
            <v-img
              src="https://cdn-icons-png.flaticon.com/512/5064/5064889.png"
              alt="Logo"
              max-width="74"
              max-height="64"
              class="mx-auto mb-4"
            ></v-img>
            
            <p class="text-h5 font-weight-bold white--text mb-8">ใช้งานโดยไม่ต้องเข้าสู่ระบบ</p>
            
            <v-btn
              block
              x-large
              color="pink lighten-4"
              class="mb-4"
              @click="$router.push('/DocumentForm')"
            >
              ส่งเอกสารแบบไม่เข้าสู่ระบบ
            </v-btn>
            
            <p class="text-h6 font-weight-bold white--text my-4">หรือ</p>
            
            <v-btn
              block
              x-large
              color="pink lighten-4"
              @click="$router.push('/DashboardPage')"
            >
              LOGIN WITH LINE
            </v-btn>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>