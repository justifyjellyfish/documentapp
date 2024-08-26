<template>
  <v-container fluid>
    <v-row justify="center">
      <v-col cols="12" md="10" lg="8">
        <h1 class="text-h3 text-center green--text text--lighten-3 mb-6">ฟอร์มส่งเอกสาร</h1>
        
        <v-form @submit.prevent="submit">
          <v-card class="mb-6 pa-4" outlined>
            <v-card-title class="text-h5">ข้อมูลผู้ส่ง</v-card-title>
            <v-text-field v-model="formData.name_source" label="ชื่อ" outlined></v-text-field>
            <v-text-field v-model="formData.email_source" label="อีเมล" outlined></v-text-field>
            <v-text-field v-model="formData.number_source" label="เบอร์โทรศัพท์" outlined></v-text-field>
            <v-menu
              v-model="dateMenu"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="formData.date_source"
                  label="วันที่"
                  prepend-icon="mdi-calendar"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                  outlined
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="formData.date_source"
                @input="dateMenu = false"
              ></v-date-picker>
            </v-menu>
          </v-card>

          <v-card class="mb-6 pa-4" outlined>
            <v-card-title class="text-h5">ข้อมูลผู้รับ</v-card-title>
            <v-select
              v-model="formData.name_destination"
              :items="[
                { text: 'teacher1', value: '1' },
                { text: 'teacher2', value: '2' },
                { text: 'teacher3', value: '3' },
              ]"
              label="ชื่อ"
              outlined
            ></v-select>
          </v-card>

          <v-card class="mb-6 pa-4" outlined>
            <v-card-title class="text-h5">เอกสาร</v-card-title>
            <v-textarea v-model="formData.detail" label="รายละเอียด" outlined rows="5"></v-textarea>
            <v-file-input label="แนบภาพเอกสาร" outlined class="mt-4"></v-file-input>
            
            <v-card-subtitle class="pt-4 pb-0">ประเภทเอกสาร</v-card-subtitle>
            <v-checkbox v-model="formData.document_type_1" label="ไม่สำคัญ"></v-checkbox>
            <v-checkbox v-model="formData.document_type_2" label="สำคัญ"></v-checkbox>
            <v-checkbox v-model="formData.document_type_3" label="ต้องการรายเซ็น"></v-checkbox>
            <v-checkbox v-model="formData.document_type_4" label="เร่งด่วน"></v-checkbox>
            <v-menu
              v-if="formData.document_type_4"
              v-model="urgentDateMenu"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="formData.document_type_4_date"
                  label="ภายในวันที่"
                  prepend-icon="mdi-calendar"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                  outlined
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="formData.document_type_4_date"
                @input="urgentDateMenu = false"
              ></v-date-picker>
            </v-menu>
          </v-card>

          <v-btn
            type="submit"
            color="pink lighten-4"
            x-large
            block
            @click="navigateToLiff"
          >
            ส่ง
          </v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'UntrackPage',
  setup() {
    const formData = ref({
      date_source: new Date().toISOString().substr(0, 10),
      detail: '',
      document_type_1: false,
      document_type_2: false,
      document_type_3: false,
      document_type_4: false,
      document_type_4_date: '',
      name_source: '',
      number_source: '',
      email_source: '',
      name_destination: '',
      number_destination: '',
      email_destination: '',
    })

    const dateMenu = ref(false)
    const urgentDateMenu = ref(false)

    function submit() {
      // Implement your submit logic here
      console.log('Form submitted:', formData.value)
    }

    function navigateToLiff() {
      // Implement navigation logic here
      console.log('Navigating to Liff')
      // For example:
      // window.location.href = '/Liff'
    }

    return {
      formData,
      dateMenu,
      urgentDateMenu,
      submit,
      navigateToLiff
    }
  }
}
</script>