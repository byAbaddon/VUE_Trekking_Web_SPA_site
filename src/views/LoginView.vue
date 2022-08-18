<script setup>

const onBtnLogin = e => {
  const username = e.target[0].value
  const password = e.target[1].value
  console.log(username, password);
 }
</script>


<template>
  <div>
    <form @submit.prevent="onBtnLogin">
      <div class="text-center">
        <h1 class="h3 mb-3 font-weight-normal">Login</h1>
      </div>
      <div class="form-label-group">
        <input
          autofocus
          type="text"
          id="inputUsername"
          name="username"
          class="form-control"
          placeholder="Username"
          required
        />
        <label for="inputUsername">Username</label>
      </div>

      <div class="form-label-group">
        <input
          type="password"
          id="inputPassword"
          name="password"
          class="form-control"
          placeholder="Password"
          required
        />
        <label for="inputPassword">Password</label>
      </div>

      <button class="btn btn-lg btn-dark btn-block" type="submit">
        <p>Sign In</p>
      </button>

      <div class="text-center mb-4">
        <p class="alreadyUser">
          Don't have account? Then just
           <router-link to="/register">
            <a href="#">Sign-Up</a>!
           </router-link>
        </p>
      </div>

      <p class="mt-5 mb-3 text-muted text-center">
        © The Trekking Zone - 2022.
      </p>
    </form>
  </div>
</template>


<style>
</style>