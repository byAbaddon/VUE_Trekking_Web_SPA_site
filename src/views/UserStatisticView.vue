<script setup>
import { useDataStore } from "@/stores/userData";
import { useTrekStore } from "../stores/treks.js";
const trekStore = useTrekStore()    
const userData = useDataStore()

</script>

<template>
  <div>
     <div class="profile col-md-6 text-center col-lg">
    <img  style="border-radius:6px"  class="profile-img" alt="Avatar" :src="userData.data.photoURL"/>
   
    <div class="profile-info">
      <p>Username: <big>{{userData.data.displayName}}</big></p>
      <p class="infoType">Wished <span class="text-brown-darken-2" >({{trekStore.allTreks.length}})</span> treks =)</p>
        <div v-if="trekStore.allTreks.length">
          <ul v-for="(trek, index) in trekStore.allTreks" :key="index"   style="list-style-type: none;">
            <li :class="index & 1 ? 'text-yellow-darken-4' : 'text-teal'" >
              {{trek.name}}
            </li>
          </ul>
           </div>
          <div v-else>
             <p   class="text-red">You, No treks yet!</p>
          </div>
    </div>
  </div>
  </div>
</template>

 