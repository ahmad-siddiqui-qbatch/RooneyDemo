<template>
  <div class="login-wraper">
    <v-row style="height: 100vh; overflow: scroll;">
      <v-col cols="0" md="6" class="pa-0 position-relative d-none d-md-block">
        <v-img
          class="login-img h-100"
          src="@/assets/loginImg.jpeg"
          cover
        ></v-img>
        <div class="img-overlay-text">
          <h2 class="text-lg fw-800 pa-10 text-white mb-10">
            Roney Innovations is a top 3% ecommerce company who holds direct
            contracts with some of America's largest retailers.
          </h2>
        </div>
      </v-col>
      <v-col cols="12" md="6" class="pa-10">
        <div class="login-form-wrapper">
          <v-img class="logo-img" src="@/assets/logo.png" contain></v-img>
          <div class="w-100">
            <AuthForms  class="login-forms"/>
          </div>
        </div>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import AuthForms from "@/components/AuthForms.vue";
export default {
  components: {
    AuthForms,
  },
};
</script>
<style lang="scss">
.login-img::before {
  background: rgb(255, 255, 255);
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(0, 0, 0, 1) 94%
  );
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
.login-wrapper {
  height: 100vh;
  overflow: auto;
}
.v-img.logo-img {
  img {
    height: 20px;
    width: auto;
  }
}
.login-form-wrapper{
  max-width: 450px;
  height: 100%;
  margin: auto;
  .login-forms{
    padding: 150px 0;
  }
}
.img-overlay-text {
  position: absolute;
  display: flex;
  align-items: flex-end;
  height: 100%;
  top: 0;
}
</style>
