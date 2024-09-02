<template>
  <v-app>
    <v-main>
      <router-view />
      <v-bottom-navigation>
        <v-btn value="recent" @click="$router.push('/')">
          <v-icon>mdi-history</v-icon>
          <span>Back</span>
        </v-btn>
      
        <v-btn value="favorites" @click="$router.push('/DashboardPage')">
          <v-icon>mdi-heart</v-icon>
          <span>Dashboard</span>
        </v-btn>
      
        <v-btn value="nearby" @click="$router.push('/DocumentForm')">
          <v-icon>mdi-map-marker</v-icon>
          <span>Form</span>
        </v-btn>
      </v-bottom-navigation>
    </v-main>
  </v-app>
</template>

<script setup>
  
</script>
