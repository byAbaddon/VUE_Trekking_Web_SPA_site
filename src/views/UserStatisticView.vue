<script setup>
import { useDataStore } from "@/stores/userData";
// import { useTrekStore } from "../stores/treks.js";
// const trek = useTrekStore()    

const userData = useDataStore()

</script>

<template>
  <div>
     <div class="profile col-md-6 text-center col-lg">
    <img  style="border-radius:6"  class="profile-img"  :src="userData.data.photoURL || '../assets/images/user.png'" alt="Avatar"/>
    <div class="profile-info">
      <p>Username: <big>{{userData.data.displayName}}</big></p>
      <p class="infoType">Wished 0 treks =)</p>
        <div v-if="1">
          <ul style="list-style-type: none;">
            <li> <p>Everest Base Camp</p></li>
            <li>  <p>Langtang and Gosainkund</p></li>
          </ul>
           </div>
          <div v-else>
             <p   class="text-red">You, No treks yet!</p>
          </div>
        
       
          
        
     
    </div>
  </div>
  </div>
</template>

 