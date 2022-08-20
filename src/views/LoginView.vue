<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import singUser  from "../service/login"; 
import getUserProfileData from "@/service/getUserProfileData";
import { useDataStore } from "../stores/userData";

const userData = useDataStore()
const storeLoginFnc =  userData.login
const router = useRouter()
const checkLogin = ref(true)


const onBtnLogin = e => {
  const username = e.target[0].value
  const password = e.target[1].value


  singUser(username, password).then(message => {
    if (message == "success") {
      getUserProfileData().then(userData => {
        //getUserDataFromRegisterProfile
        const [userName, userPhoto] = userData
        console.log(userName, userPhoto)
        router.push('/')
         storeLoginFnc()
         console.log( 'data from store' ,   userData.then(e => console.log(e)));

      })
    } else {
      checkLogin.value = false
      setTimeout(() => {
         document.getElementById('loginFrom').reset()
         checkLogin.value = true
      }, 2000);
    }
  })

   }
</script>


<template>
  <div style="width: 70%;margin: 0 auto; margin-top:2em"  >
    <form id="loginFrom"   @submit.prevent="onBtnLogin">
      <div class="text-center">
        <h1 class="h3 mb-3 font-weight-normal">Login</h1>
      </div>
      <div class="form-label-group" >
        <input
          autofocus
          type="email"
          id="inputUsername"
          name="email"
          class="form-control"
          placeholder="Email"
          required
        />
        <label for="inputUsername">Email</label>
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
      <div>
      <button v-if="checkLogin" class="btn btn-lg btn-dark btn-block" type="submit">
        <p>Sign In</p>
      </button>
      <v-alert v-else type="error">'Error! Fail to login. Wrong email or password...'</v-alert>
      </div>   
      

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