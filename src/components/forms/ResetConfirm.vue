<template>
  <div>
    <v-card flat>
      <v-card-title class="text-lg fw-800">Password Reset</v-card-title>
      <v-card-subtitle class="text-xs pt-2 pb-3"
        >Your password has been successfully reset. Click below to log in
        magically.</v-card-subtitle
      >
      <v-img
        src="@/assets/success.png"
        class="email-img mx-auto my-5"
      ></v-img>
      <v-card-actions>
        <v-btn
          class="form-btn bg-primary mt-5 pa-0"
          flat
          @click="NewPasswordForm"
          >Continue</v-btn
        >
      </v-card-actions>
    </v-card>
  </div>
</template>


<script>
export default {
  methods: {
    NewPasswordForm() {
      this.$emit("change-form", "SignInForm");
    },
  },
};
</script>
<style lang="scss">
.email-img {
  width: 240px;
  height: auto;
}
</style>