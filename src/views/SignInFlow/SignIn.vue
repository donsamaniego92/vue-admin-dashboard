<template>
  <div
    class="container"
    :class="{'light-background' : !isDarkMode, 'dark-background' : isDarkMode}"
  >
    <RequestAccount/>
    <div class="login">
      <img src="@/assets/ppilogo.png" v-show="isDarkMode">
      <img src="@/assets/ppilogo.png" v-show="!isDarkMode">
      <h4 :class="{'light-text' : isDarkMode, 'dark-text' : !isDarkMode}">Sign into PPI Lab</h4>
      <input
        :class="{'light-field' : isDarkMode, 'dark-field' : !isDarkMode}"
        type="email"
        placeholder="Email"
      >
      <input
        :class="{'light-field' : isDarkMode, 'dark-field' : !isDarkMode}"
        type="password"
        placeholder="Password"
      >
      <button>Sign In</button>
      <router-link
        to="/recover"
        :class="{'light-link': isDarkMode, 'dark-link': !isDarkMode}"
      >Forgot Your Password?</router-link>
      <ThemeSwitch/>
    </div>
  </div>
</template>

<script>
import RequestAccount from "@/components/RequestAccount";
import ThemeSwitch from "@/components/ThemeSwitch";

export default {
  name: "SignIn",
  components: {
    RequestAccount,
    ThemeSwitch
  },

  computed: {
    isDarkMode() {
      return this.$store.getters.isDarkMode;
    }
  },
  methods: {
    toggleDarkMode() {
      this.$store.commit("toggleDarkMode");
    }
  }
};
</script>

<style scoped lang="scss">
.container {
  display: flex;
  justify-content: center;
  align-items: center;

  min-height: 100vh;
}

.login {
  width: 400px;
}
</style>