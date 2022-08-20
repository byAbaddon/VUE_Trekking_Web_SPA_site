
<script setup>
</script>

<template>
  <div class="bg-grey-darken-3">
    <nav class="site-header sticky-top py-1 mb-0">
      <v-icon color="yellow-darken-3" size="30" class="mt-1 ml-4"    > mdi-image-filter-hdr</v-icon> 
      <div v-if="1"  class="ml-12 container d-flex float-right"> 
        <router-link to="/login">
          <a class="header-hover py-2 d-none d-md-inline-block mr-12">Login</a>
        </router-link>
 
        <router-link to="/register">
          <a class="header-hover py-2 d-none d-md-inline-block mr-12">Register</a>
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