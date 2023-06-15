<template>
  <div>
    <component :is="currentForm" @change-form="changeForm" />
  </div>
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