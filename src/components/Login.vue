<template>
  <div class="container-fluid login-page min-vh-100">
    <div class="row px-0 d-flex flex-row min-vh-100">
      <div
        class="col-xs-12 col-md-4 d-flex flex-column col-lg-4 align-items-center align-self-center"
      >
        <img class="logo mb-5" alt="logo" src="../assets/logo-white.svg" />
        <form v-on:submit.prevent="onSubmit">
          <div class="mb-3">
            <label for="Email" class="form-label">Email address</label>
            <input
              type="email"
              class="form-control"
              id="Email1"
              aria-describedby="emailHelp"
              placeholder="Enter your e-mail"
            />
            <div id="emailHelp" class="form-text"></div>
          </div>
          <label for="password" class="form-label">Password</label>

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
                      'fa-eye-slash': showPassword,
                      'fa-eye': !showPassword,
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
      <div class="col px-0 img-container">
        <img
          class="img-gallery img-fluid"
          src="../assets/images/laura-nyhuis-0P_pT8ZQKd8-unsplash.jpg"
          alt=""
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
}
label {
  display: flex;
  color: #fff;
}
.img-container {
  overflow: hidden;
}
.img-gallery {
  height: 100%;
  overflow: hidden;
  object-fit: cover;
  animation: zoomin 10s infinite;
}

@keyframes zoomin {
  0% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1.3);
  }
}
</style>
