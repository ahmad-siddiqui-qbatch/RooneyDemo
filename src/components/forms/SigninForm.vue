<template>
  <v-card flat>
    <v-card-title class="text-lg fw-800">Sign-in</v-card-title>
    <v-card-subtitle class="text-xs pt-2 pb-3">Login with your email and password.</v-card-subtitle>
    <v-card-text>
      <v-form ref="form" @submit.prevent="login">
        <label for="username" class="form-label">Username</label>
        <input v-model="username" type="text" name="username" placeholder="Enter Username Here" class="w-100 input-form-control mb-5" @click="clearError" @keydown.enter="login">
        <label for="password" class="form-label">Password</label>
        <div class="password-input-wrapper">
          <input v-model="password" :type="showPassword ? 'text' : 'password'" name="password" placeholder="Enter Password" class="w-100 input-form-control" @click="clearError" @keydown.enter="login">
          <i class="password-toggle-icon" :class="showPassword ? 'mdi mdi-eye' : 'mdi mdi-eye-off'" @click="togglePasswordVisibility"></i>
        </div>
        <p v-if="errorMessage" class="text-red">{{ errorMessage }}</p>
        <v-card-actions class="pa-0">
          <v-btn class="ms-auto text-primary pa-0" @click="showForgotPasswordForm">Forgot Password</v-btn>
        </v-card-actions>
        <v-btn class="form-btn bg-primary mt-5" flat type="submit">Login</v-btn>
      </v-form>
    </v-card-text>
    <v-card-actions>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      errorMessage: '',
      showPassword: false,
    };
  },
  methods: {
    login() {
      if (this.username === '' || this.password === '') {
        this.errorMessage = 'Please enter Username and Password';
      } else if (this.username === 'admin' && this.password === 'admin') {
        // Redirect to Home.vue page
        this.$router.push({ name: 'Home' });
        this.errorMessage = '';
      } else {
        // Show error message
        this.errorMessage = 'Username or Password is incorrect';
      }
    },
    showForgotPasswordForm() {
      this.$emit('change-form', 'ForgotPasswordForm');
    },
    clearError() {
      this.errorMessage = '';
    },
    togglePasswordVisibility() {
      this.showPassword = !this.showPassword;
    },
    // Your other methods here
  },
};
</script>

<style lang="scss">
.text-red {
  color: red;
}

.password-input-wrapper {
  position: relative;
}

.password-toggle-icon {
  position: absolute;
  right: 12px;
  font-size: 20px;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
}
.v-form{
  width: 100%;
}
</style>
