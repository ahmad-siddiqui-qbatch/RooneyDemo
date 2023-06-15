<template>
  <v-row class="h-100">
    <v-col cols="6" class="pa-0">
      <v-img class="login-img h-100" src="@/assets/loginImg.jpeg" cover></v-img>
    </v-col>
    <v-col cols="6" class="pa-10">
      <v-img class="logo-img" src="@/assets/logo.png" contain></v-img>
          <div class="d-flex align-center justify-center h-100">
            <div class="w-100">
              <component :is="currentForm" @change-form="changeForm" />
            </div>
          </div>
    </v-col>
  </v-row>
</template>

<script>
import SignInForm from '@/components/forms/SigninForm.vue';
import ForgotPasswordForm from '@/components/forms/ForgotPasswordForm.vue';
import EmailForm from '@/components/forms/EmailForm.vue';
import NewPasswordForm from '@/components/forms/NewPasswordForm.vue';
import ResetConfirm from '@/components/forms/ResetConfirm.vue';

export default {
  components: {
    SignInForm,
    ForgotPasswordForm,
    EmailForm,
    NewPasswordForm,
    ResetConfirm,
  },
  data() {
    return {
      currentForm: 'SignInForm'
    };
  },
  methods: {
    changeForm(formName) {
      this.currentForm = formName;
    }
  }
};
</script>


<style lang="scss">
.login-img::before{
  background: rgb(255,255,255);
  background: linear-gradient(180deg, rgba(255,255,255,0) 0%, rgba(0,0,0,1) 94%);
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
.v-img.logo-img{
  position: absolute;
  img{
    height: 20px;
  width: auto;
  }
}
</style>
