
<script setup>
</script>

<template>
  <div class="bg-grey-darken-3">
    <nav class="site-header sticky-top py-1 mb-0">
      
      <img
        class="logo-image"
        src="../assets/images/logo.png"
        alt="logo"
        style="width: 4%"
      />
      <div v-if="0"  class="ml-12 container d-flex justify-space-between">
        <br>
        <router-link to="/login">
          <a class="header-hover py-2 d-none d-md-inline-block">Login</a>
        </router-link>
        <router-link to="/register">
          <a class="header-hover py-2 d-none d-md-inline-block">Register</a>
        </router-link>
      </div>

      <div v-else class="ml-12 container d-flex justify-space-between">
        <br>
        <router-link to="/add-trek">
          <a class="header-hover py-2 d-none d-md-inline-block">RequestTrek</a>
        </router-link>
        <router-link to="/user-statistic">
          <a class="header-hover py-2 d-none d-md-inline-block"
            >Hello, username</a
          >
        </router-link>
        <router-link to="/">
          <a class="header-hover py-2 d-none d-md-inline-block">Logout</a>
        </router-link>
      </div>
    </nav>
  </div>
</template>

<style  scoped>
img {
  left: 25px;
}
</style>