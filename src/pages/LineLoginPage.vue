<template>
    <v-card
      class="mx-auto"
      prepend-icon="$vuetify"
      subtitle=""
      width="400"
    >
      <template v-slot:title>
        <span class="font-weight-black">วิธีเข้าสู่ระบบด้วย Line</span>
      </template>
  
      <v-card-text class="bg-surface-light pt-4">เปิด Line</v-card-text>
      <div class="ma-4">
        <div class="text-subtitle-2">Cover</div>
        <v-img
          :aspect-ratio="1"
          class="bg-white"
          src="../assets/logo.png"
          width="300"
          cover
        ></v-img>
      </div>
      <v-card-text class="bg-surface-light pt-4">เปิดการแสกน QR code</v-card-text>
      <div class="ma-4">
        <div class="text-subtitle-2">Cover</div>
        <v-img
          :aspect-ratio="1"
          class="bg-white"
          src="https://www.hardreset.info/media/resetinfo/2021/042/e8252770877e4173bed800617d8b2c92/apps-line.jpg"
          width="300"
          cover
        ></v-img>
      </div>
    </v-card>
  </template>   