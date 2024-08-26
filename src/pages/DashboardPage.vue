<template>
    <v-container fluid>
      <v-card class="mb-6">
        <v-row no-gutters align="center" class="pa-4">
          <v-col cols="auto">
            <v-avatar size="100">
              <v-img :src="lineImage" alt="User"></v-img>
            </v-avatar>
          </v-col>
          <v-col class="pl-4">
            <v-list-item three-line>
              <v-list-item-content>
                <v-list-item-title>ชื่อ: {{ lineName }}</v-list-item-title>
                <v-list-item-subtitle>เบอร์:</v-list-item-subtitle>
                <v-list-item-subtitle>uid: {{ lineUID }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-btn @click="change_infomation" text color="primary">แก้ไขข้อมูล</v-btn>
          </v-col>
        </v-row>
      </v-card>
  
      <h2 class="text-h5 font-weight-bold text-center green--text text--lighten-3 mb-4">เอกสารที่ยังไม่รับ</h2>
      <v-card class="mb-6">
        <v-list>
          <v-list-item v-for="item in itmes" :key="item.id">
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card>
  
      <h2 class="text-h5 font-weight-bold text-center red--text text--lighten-3 mb-4">เอกสารที่รับแล้ว</h2>
      <v-card>
        <v-list>
          <v-list-item v-for="item in itmes" :key="item.id">
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card>
  
      <v-btn
        fab
        color="primary"
        fixed
        bottom
        right
        @click="$router.push('./untrack')"
      >
        <v-icon>mdi-plus</v-icon>
      </v-btn>
    </v-container>
  </template>
  
  <script>
  import liff from "@line/liff";
import { ref, onMounted } from 'vue';
import { useRouter } from 'vue-router';

export default {
  setup() {
    const router = useRouter();
    const lineName = ref('');
    const lineUID = ref('');

    const initializeLiff = async () => {
      try {
        await liff.init({ liffId: '2005937488-5q2Kd2lk' });
        if (!liff.isLoggedIn()) {
          liff.login();
        } else {
          const profile = await liff.getProfile();
          lineName.value = profile.displayName;
          lineUID.value = profile.userId;
        }
      } catch (error) {
        console.error('LIFF initialization failed', error);
      }
    };

    onMounted(() => {
      initializeLiff();
    });

    const change_infomation = () => {
      // Implement your logic for changing information
    };

    return {
      lineName,
      lineUID,
      change_infomation,
    };
  },
};
  </script>