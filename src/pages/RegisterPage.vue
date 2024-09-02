<template>
  <v-container fluid>
    <v-row justify="center">
      <v-col cols="12" md="8" lg="6">
        <h1 class="text-h3 text-center green--text text--lighten-3 mb-6">Register</h1>
        
        <v-form @submit.prevent="register">
          <v-card class="mb-6 pa-4" outlined>
            <v-card-title class="text-h5">User Information</v-card-title>
            <v-text-field v-model="formData.username" label="Username" outlined></v-text-field>
            <v-text-field v-model="formData.email" label="Email" outlined></v-text-field>
            <v-text-field v-model="formData.password" label="Password" type="password" outlined></v-text-field>
            <v-text-field v-model="formData.confirmPassword" label="Confirm Password" type="password" outlined></v-text-field>
          </v-card>

          <v-btn type="submit" color="primary" class="mr-4">Register</v-btn>
          <v-btn type="reset" color="secondary">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        username: '',
        email: '',
        password: '',
        confirmPassword: ''
      }
    };
  },
  methods: {
    async register() {
      try {
        const response = await fetch('http://localhost:5000/api/items', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(this.formData),
        });

        if (response.ok) {
          console.log('User registered successfully');
          // Handle success (e.g., navigate to another page or show a success message)
        } else {
          console.error('Failed to register user');
          // Handle error (e.g., show an error message)
        }
      } catch (error) {
        console.error('Error registering user:', error);
        // Handle error (e.g., show an error message)
      }
    }
  }
}
</script>
