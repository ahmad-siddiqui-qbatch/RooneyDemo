<template>
  <div>
    <v-card flat>
      <v-card-title class="text-lg fw-800">Check Your Email</v-card-title>
      <v-card-subtitle class="text-xs pt-2 pb-3"
        >We sent a password reset link to
        <strong>account@roneyinnovation.com</strong></v-card-subtitle
      >
      <v-img
        src="@/assets/email-img.png"
        class="email-img mx-auto my-5"
      ></v-img>
      <v-card-actions>
        <v-btn class="form-btn bg-primary mt-5 pa-0" flat @click="NewPasswordForm">Reset Password</v-btn>
      </v-card-actions>
      <v-card-text class="text-center pt-2">If you didn’t receive the email please <a href="#">Click here</a></v-card-text>
    </v-card>
  </div>
</template>


<script>
export default {
  methods : {
    NewPasswordForm() {
      this.$emit('change-form', 'NewPasswordForm')
    },
  }
}
</script>
<style lang="scss">
.email-img {
  width: 250px;
  height: auto;
}
</style>