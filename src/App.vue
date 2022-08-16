<script setup>
import { defineComponent } from "vue";
import HeaderComponent from "@/components/HeaderComponent.vue";
import FooterComponent from "@/components/FooterComponent.vue";

defineComponent(() => {
  HeaderComponent, FooterComponent;
});
</script>



<template>
  <div>
    <HeaderComponent />
    <main>
      <img
        alt="Vue logo"
        class="logo"
        src="@/assets/logo.svg"
        width="125"
        height="125"
      />

  

      <FooterComponent/>
    </main>
  </div>
</template>
