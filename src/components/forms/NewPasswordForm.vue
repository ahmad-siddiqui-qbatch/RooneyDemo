<template>
  <div>
    <v-card flat>
      <v-card-title class="text-lg fw-800">Reset Password</v-card-title>
      <v-card-subtitle class="text-xs pt-2 pb-3">
        Your new password must be different from previously used passwords
      </v-card-subtitle>
      <v-card-text>
        <v-form>
          <!-- Password input field -->
          <div class="d-flex align-center justify-space-between">
            <label for="password" class="form-label">Password</label>
            <div class="password-strength-bar pb-2">
              <span class="text-xs pe-1">Strength: </span>
              <div
                v-for="index in 10"
                :key="index"
                :class="{ filled: index <= passwordStrength }"
                class="pill"
              ></div>
            </div>
          </div>
          <div class="position-relative">
            <input
              v-model="password"
              :type="showPassword ? 'text' : 'password'"
              placeholder="Enter Password"
              class="w-100 input-form-control"
              @blur="clickOutside"
              @input="calculatePasswordStrength"
              @keydown.enter.prevent="submitForm"
            />
            <!-- Password visibility toggle -->
            <v-icon
              v-if="!showPassword"
              @click="showPassword = !showPassword"
              class="password-icon mdi"
            >
              <span class="mdi mdi-eye-off-outline"></span>
            </v-icon>
            <v-icon
              v-else
              @click="showPassword = !showPassword"
              class="password-icon mdi"
            >
              <span class="mdi mdi-eye-outline"></span>
            </v-icon>
          </div>
          <span v-if="showErrorMessage" class="text-xs pt-1 d-block error-message">
            {{ errorMessage }}
          </span>

          <!-- Confirm Password input field -->
          <label for="confirm-password" class="form-label mt-4">Confirm Password</label>
          <div class="position-relative">
            <input
              v-model="confirmPassword"
              :type="showConfirmPassword ? 'text' : 'password'"
              placeholder="Enter Confirm Password"
              class="w-100 input-form-control"
              @keydown.enter.prevent="submitForm"
            />
            <!-- Confirm Password visibility toggle -->
            <v-icon
              v-if="!showConfirmPassword"
              @click="showConfirmPassword = !showConfirmPassword"
              class="password-icon mdi"
            >
              <span class="mdi mdi-eye-off-outline"></span>
            </v-icon>
            <v-icon
              v-else
              @click="showConfirmPassword = !showConfirmPassword"
              class="password-icon mdi"
            >
              <span class="mdi mdi-eye-outline"></span>
            </v-icon>
          </div>
          <div v-if="passwordMatched && confirmPassword !== ''" class="success-message">
            Password matched
          </div>
        </v-form>
        <!-- Reset Password button -->
        <v-btn @click="submitForm" class="form-btn bg-primary mt-10" flat>
          Reset Password
        </v-btn>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      password: "",
      confirmPassword: "",
      showErrorMessage: false,
      showPassword: false,
      showConfirmPassword: false,
      clickedOutside: false,
      passwordStrength: 0,
      errorMessage: "Password must be at least 6 characters long",
    };
  },
  computed: {
    passwordMatched() {
      return this.password === this.confirmPassword;
    },
    passwordStrengthPercentage() {
      return this.passwordStrength * 10;
    },
    isValidForm() {
      return (
        this.isValidPassword() && this.passwordMatched && this.confirmPassword !== ""
      );
    },
  },
  methods: {
    clickOutside() {
      this.clickedOutside = true;
      if (!this.isValidPassword()) {
        this.showErrorMessage = true;
      }
    },
    isValidPassword() {
      return this.password.length >= 6;
    },
    calculatePasswordStrength() {
      const pairCount = Math.floor(this.password.length / 2);
      this.passwordStrength = Math.min(pairCount, 10);
    },
    submitForm() {
      if (this.clickedOutside) {
        this.showErrorMessage = !this.isValidPassword();
        this.calculatePasswordStrength();
      }
      if (this.isValidForm) {
        this.$emit('change-form', 'ResetConfirm');
      }
    },
  },
  watch: {
    password() {
      if (this.clickedOutside) {
        this.showErrorMessage = !this.isValidPassword();
        this.calculatePasswordStrength();
      }
    },
  },
};
</script>

<style>
.password-icon {
  position: absolute;
  top: 50%;
  right: 0.5rem;
  transform: translateY(-50%);
  cursor: pointer;
}
.success-message {
  color: green;
}
.error-message {
  color: red;
}
.password-strength-bar {
  display: flex;
  align-items: center;
  margin-top: 10px;
}

.pill {
  width: 16px;
  height: 4px;
  margin-right: 2px;
  background-color: #ccc;
  margin-left: 2px;
  border-radius: 10px;
}

.filled {
  background-color: #6abf63;
}
</style>
