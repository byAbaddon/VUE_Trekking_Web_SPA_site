<script setup>
import singUser  from "../service/login"; 
import getUserProfileData from "@/service/getUserProfileData";

const onBtnLogin = e => {
  const username = e.target[0].value
  const password = e.target[1].value


  singUser(username, password).then(message => {
    if (message == "success") {
      getUserProfileData().then(userData => {
        //getUserDataFromRegisterProfile
        const [userName, userPhoto] = userData

        console.log(userName, userPhoto)
      })
    }
  })

   }
</script>


<template>
  <div style="width: 70%;margin: 0 auto; margin-top:2em"  >
    <form @submit.prevent="onBtnLogin">
      <div class="text-center">
        <h1 class="h3 mb-3 font-weight-normal">Login</h1>
      </div>
      <div class="form-label-group" >
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
          minlength="6"
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