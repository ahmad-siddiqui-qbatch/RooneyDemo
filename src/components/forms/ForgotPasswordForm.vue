<template>
  <div>
    <v-card flat>
      <v-card-title class="text-lg fw-800">Forgot Password</v-card-title>
      <v-card-subtitle class="text-xs pt-2 pb-3">
        Enter your registered email address to change your Roney innovation account password.
      </v-card-subtitle>
      <v-card-text>
        <v-form ref="form">
          <label for="email" class="form-label">Email</label>
          <input
            v-model="email"
            type="text"
            class="input-form-control w-100"
            placeholder="Enter Email Here"
            @focus="clearError"
            @keydown.enter.prevent="resetPassword"
          />
          <p v-if="showErrorMessage" class="text-red">Please enter a valid email address.</p>
        </v-form>
        <v-btn class="form-btn bg-primary mt-10" flat @click="resetPassword">Reset Password</v-btn>
        <v-card-actions>
          <v-btn class="ma-auto text-primary pa-0" @click="showSignInForm">
            <span class="mdi mdi-arrow-left-thin"></span> Back to login
          </v-btn>
        </v-card-actions>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      showErrorMessage: false,
    };
  },
  methods: {
    validateEmail() {
      const regex = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
      this.showErrorMessage = !regex.test(this.email);
    },
    showSignInForm() {
      this.$emit('change-form', 'SignInForm');
    },
    clearError() {
      this.showErrorMessage = false;
    },
    resetPassword() {
      this.validateEmail(); // Validate the email before resetting the password
      if (!this.showErrorMessage) {
        this.$emit('change-form', 'EmailForm');
      }
    },
  },
};
</script>

<style>
.text-red {
  color: red;
}
</style>
