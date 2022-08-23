<script setup>
import { useDataStore } from "../stores/userData";
import { useTrekStore } from "../stores/treks";
import { updateData } from "../service/updateData";
import { useRouter, useRoute } from "vue-router";
import { ref } from "vue";

const trekStore = useTrekStore();
const userData = useDataStore();
const router = useRouter();
const routeTrekId = useRoute().params.id;
let { organizer, id, imageURL, date, description, location, likes, voters } =
  trekStore.allTreks.find((x) => x.id == routeTrekId);
let currentLikes = ref(likes);
let typeMessage = ref("");
let messageAlert = ref("");

const onBtnExit = () => router.go(-1);

const onBtnEdit = (e) => {
  console.log(e.currentTarget.textContent, "edit");
};

const onBtnDelete = (e) => {
  console.log(id);
  // console.log({...currentTrek.value } , "delete");
};

const onBtnLike = (e) => {
  //checking if he has already in liked list

  let check = voters.includes(userData.data.uid);
  if (!check) {
    currentLikes.value++;
    likes += 1;
    voters.push(userData.data.uid);
    updateData(routeTrekId, { organizer, id, imageURL, date, description, location, likes, voters, })
      .then((e) => console.log("Success update"))
      .catch((e) => console.log(e.error));
    typeMessage.value = "success";
  } else {
    typeMessage.value = "error";
    console.log("You already liked this trek!");
  }
  setTimeout(() => {
    typeMessage.value = messageAlert.value = "";
  }, 2000);
};
</script>

<template>
  <div style="width: 80%; margin: 0 auto; margin-top: 1em; margin-bottom: 2em">
    <div class="row single-trek-details text-center">
      <div class="col-md-12 text-center overflow-hidden">
        <img class="details-img" style="border-radius: 6px" :src="imageURL" />
        <div class="overflow-hidden my-3 p-3">
          <h2 class="display-5">{{ location }}</h2>
          <p class="infoType">Description:</p>
          <p class="trek-description">{{ description }}</p>
          <p class="infoType">
            Date: <span>{{ date }}</span>
          </p>
          <p class="infoType">
            Likes: <span>{{ currentLikes }}</span>
          </p>
          <p class="infoType">
            Organizer: <span>{{ userData.data.displayName }}</span>
          </p>
        </div>

        <!-- check is owner--->
        <div v-if="organizer == userData.data.uid" class="buttons-together">
          <div v-if="!typeMessage">
            <v-btn @click="onBtnEdit" variant="outlined">
              Edit the trek
              <v-icon color="black-darken-3" size="30">
                mdi-hammer-screwdriver</v-icon
              >
            </v-btn>

            <v-btn class="mx-4" @click="onBtnDelete" variant="outlined">
              Delete the trek
              <v-icon color="red-darken-3" size="30"> mdi-close-circle </v-icon>
            </v-btn>
            <v-btn @click="onBtnExit" variant="outlined">
              Exit
              <v-icon color="blue-darken-3" size="30"> mdi-exit-run</v-icon>
            </v-btn>
          </div>

          <div v-else>
            <v-alert :type="typeMessage">Thank you for like!</v-alert>
          </div>
        </div>

        <!-- no owner  able to make like -->
        <div v-else>
          <div v-if="!typeMessage">
            <v-btn class="mr-6" @click="onBtnLike" variant="outlined">
              Like
              <v-icon color="yellow-darken-3" size="30"> mdi-heart</v-icon>
            </v-btn>
            <v-btn @click="onBtnExit" variant="outlined">
              Exit
              <v-icon color="blue-darken-3" size="30"> mdi-exit-run</v-icon>
            </v-btn>
          </div>

          <div v-else>
            <v-alert :type="typeMessage">You already liked this trek!</v-alert>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>