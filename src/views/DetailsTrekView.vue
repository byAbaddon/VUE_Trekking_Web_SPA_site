<script setup>
import { useRouter } from "vue-router";
const router = useRouter()

const onBtnExit = () => router.go(-1)

const onBtnEdit = e => {
  console.log(e.currentTarget.textContent , 'edit');
}

const onBtnDelete = e => {
  console.log(e, 'delete');
}

const onBtnLike = e => {
  console.log(e, 'like');
} 


</script>

<template>
  <div>
  <div class="row single-trek-details text-center">
    <div class="col-md-12 text-center overflow-hidden">
      <img class="details-img"
      src="https://s3.us-east-1.wasabisys.com/mts-wp-uploads/trips/trip_hero8_kha_2880x1260.jpg" />
      <div class="overflow-hidden my-3 p-3">
        <h2 class="display-5">Everest Base Camp</h2>
        <p class="infoType">Description:</p>
        <p class="trek-description">Experience beautiful Tengboche Monastery, local Sherpa hospitality, and the serenity of Buddhist culture as you trek to the top of Kala Patar. Here, behold the great Mount Everest-an epic view matched only by your incredible sense of accomplishment-before arriving at the legendary Mt. Everest Base Camp at an elevation of 17,600'.</p>
        <p class="infoType">Date: <span>26.08.2020</span></p>
        <p class="infoType">Likes: <span>0</span></p>
        <p class="infoType">Organizer: <span>username</span></p>
      </div>
      <div class = "buttons-together">

      <v-btn @click="onBtnEdit" variant="outlined" > Edit the trek
        <v-icon color="black-darken-3" size="30" >  mdi-hammer-screwdriver</v-icon> 
      </v-btn>
         
        <v-btn @click="onBtnDelete"  variant="outlined" > Close the trek
         <v-icon color="red-darken-3" size="30" > mdi-close-circle </v-icon>
      </v-btn>
     
       <v-btn @click="onBtnLike"  variant="outlined" > Like
        <v-icon color="yellow-darken-3" size="30" > mdi-heart</v-icon>
      </v-btn>
     
      <v-btn @click="onBtnExit"  variant="outlined" > Exit
        <v-icon color="blue-darken-3" size="30" > mdi-exit-run</v-icon>
      </v-btn> 
    </div>
    </div>
  </div>
  </div>
</template>