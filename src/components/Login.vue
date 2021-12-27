<template>
  <div class="container-fluid login-page min-vh-100">
    <div class="row px-0 d-flex flex-row min-vh-100">
      <div
        class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-4 d-flex flex-column col-lg-4 align-items-center align-self-center"
      >
        <div class="col-8">
          <img class="logo mb-5" alt="logo" src="../assets/logo-white.svg" />
          <form v-on:submit.prevent="onSubmit">
            <div class="mb-3">
              <label for="Email" class="form-label">E-mail</label>
              <input
                type="email"
                class="form-control"
                id="Email1"
                aria-describedby="emailHelp"
                placeholder="Enter your e-mail"
              />
              <div id="emailHelp" class="form-text"></div>
            </div>
            <div class="input-group pw-group">
              <label for="password" class="form-label">Password</label>

              <span>Forgot password?</span>
            </div>
            <div class="mb-3 input-group">
              <input
                v-if="showPassword"
                type="text"
                class="form-control"
                v-model="password"
              />
              <input
                v-else
                type="password"
                class="form-control"
                v-model="password"
              />
              <div class="input-group-append">
                <button class="button form-control" @click="toggleShow">
                  <span class="icon is-small is-right">
                    <i
                      class="fas"
                      :class="{
                        'fa-eye': showPassword,
                        'fa-eye-slash': !showPassword,
                      }"
                    ></i>
                  </span>
                </button>
              </div>
            </div>
            <div>
              <button class="btn btn-block btn-lg btn-primary">Sign in</button>
            </div>
          </form>
        </div>
      </div>
      <div class="d-none col d-lg-inline-flex d-flex px-0 img-container">
        <SlideShow></SlideShow>
      </div>
    </div>
  </div>
</template>

<script>
import SlideShow from "./SlideShow.vue";
export default {
  components: { SlideShow },
  data() {
    return {
      showPassword: false,
      password: null,
    };
  },
  computed: {
    buttonLabel() {
      return this.showPassword ? "Hide" : "Show";
    },
  },
  methods: {
    toggleShow() {
      this.showPassword = !this.showPassword;
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.login-page {
  background-color: #0f2640;
  height: auto;
  width: auto;
}
.logo {
  width: 100px;
  height: 100px;
}
.btn-block {
  width: 100%;
  padding-bottom: 15px;
  border-radius: 10px;
  padding-top: 15px;
}
input {
  padding-bottom: 10px;
  border-radius: 10px;
  padding-top: 10px;
}
.button {
  padding-bottom: 10px;
  border-radius: 0px 10px 10px 0;
  padding-top: 10px;
}
.button:focus {
  box-shadow: none;
}
.pw-group {
  justify-content: space-between;
}
.pw-group span {
  color: #a2b5cd;
}
label {
  display: flex;
  color: #fff;
}
.img-container {
  overflow: hidden;
}
</style>
