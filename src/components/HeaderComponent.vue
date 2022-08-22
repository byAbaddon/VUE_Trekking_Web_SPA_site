<script setup>
import { useDataStore } from "@/stores/userData";
import { useRoute } from "vue-router";
const userData = useDataStore()
const route = useRoute()
</script>

<template>
  <div class="bg-grey-darken-3">
    <nav class="site-header sticky-top mb-0">
      <!-- User Not Login-->
      <v-icon color="yellow-darken-3" size="30" class="mt-1 ml-4  float-start"> mdi-image-filter-hdr</v-icon> 
      <div v-if="!userData.isAuth"  class="ml-12 container d-flex float-right"> 
        <router-link to="/login">
          <a class="header-hover py-2 d-none d-md-inline-block mr-12">Login</a>
        </router-link>
 
        <router-link to="/register">
          <a class="header-hover py-2 d-none d-md-inline-block mr-12">Register</a>
        </router-link>
      </div>

     <!-- User Login-->
      <div v-else class="d-flex justify-space-around">  
       
        <router-link to="/add-trek">
          <a class="header-hover py-2 d-none d-md-inline-block">RequestTrek</a>
        </router-link>
         
        <router-link :to="`${route.name == 'user' ? '/' : '/user-statistic'}`">
          <a class="header-hover py-2 d-none d-md-inline-block"
            >Hello, <span class=" text-grey text-decoration-underline" >{{ userData.data.displayName || 'Anonymous'}}</span> </a
          >
        </router-link>
  
        <router-link to="/">
          <a @click="userData.logout" class="header-hover py-2 d-none d-md-inline-block">Logout</a>
        </router-link>
      </div>
    </nav>
  </div>
</template>

