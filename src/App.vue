<script setup>
import { useRouter} from 'vue-router'  
import HeaderComponent from '../src/components/HeaderComponent.vue'
import FooterComponent from '../src/components/FooterComponent.vue'
import { defineComponent, onBeforeMount, onMounted  } from 'vue';

defineComponent(() => { HeaderComponent, FooterComponent })
const router = useRouter()

onMounted(() => {
  if (localStorage.getItem('auth') == null) {
    router.push("/").catch(() => { })
  }

})

onBeforeMount(() => {
  window.addEventListener("beforeunload", (event) => {
    if (localStorage.getItem("auth") != null) {
      event.preventDefault();
      return;
    }
    return;
  });
});

</script>


<template>
  <v-app>
    <header-component />
    <v-main id="main">
      <router-view />
    </v-main>
    <footer-component />
  </v-app>
</template>
