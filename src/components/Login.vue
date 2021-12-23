<template>
  <div class="container-fluid login-page min-vh-100">
    <div class="row px-0 d-flex flex-row min-vh-100">
      <div
        class="col-xs-12 col-md-4 d-flex flex-column col-lg-4 align-items-center align-self-center"
      >
        <img class="logo" alt="logo" src="../assets/logo-white.svg" />
        <form>
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
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label"
              >Password</label
            >
            <div class="input-group">
              <input
                type="password"
                class="form-control"
                id="exampleInputPassword1"
                placeholder="enter your password"
              />
              <div class="input-group-append">
                <span class="input-group-text" id="basic-addon2">@</span>
              </div>
            </div>
          </div>
          <div>
            <button type="submit" class="btn btn-block btn-lg btn-primary">
              Sign in
            </button>
          </div>
        </form>
      </div>
      <div class="col px-0">
        <img
          class="img-fluid"
          src="../assets/images/laura-nyhuis-0P_pT8ZQKd8-unsplash.jpg"
          alt=""
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
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
  text-align: left;
}
img {
  height: 100%;
  overflow: hidden;
  object-fit: cover;
}
</style>
