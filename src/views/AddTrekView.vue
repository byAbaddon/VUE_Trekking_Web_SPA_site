<script setup>
const onBtnAddTrek = (e => {
  const [location , date, description, image]  = e.target
  console.log(location.value, date.value);
        // ◦add  Organizer: string representing the current trek creator;
        // ◦add  Likes: number starting from 0;
  
 })
</script>



<template>
<div class="my-5 mx-auto" style="max-width: 70rem">
   <form class="create-trek" @submit.prevent="onBtnAddTrek" >
    <div class="text-center mb-4">
      <h1 class="h3 mb-3 font-weight-normal">Wish for a new adventure!</h1>
      <p>Fill up the following information!</p>
    </div>

    <div class="form-label-group">
      <input  minlength="6"  type="text" name="location" class="form-control" placeholder="Location" required autofocus>
      <label for="inputTrekName">Location</label>
    </div>

    <div class="form-label-group">
      <input type="text"  name="dateTime" class="form-control" placeholder="Date" required>
      <label for="inputTrekDate">Date</label>
    </div>

    <div class="form-label-group" style="">
      <textarea  minlength="6"  type="text"  name="description" class="form-control bg-white pa-1" placeholder="Description" required></textarea>
      <label for="inputTrekDescription">Description</label>
    </div>

    <div class="form-label-group">
      <input type="text"  name="imageURL" class="form-control" placeholder="Image" required autofocus>
      <label for="inputTrekImage">Image</label>
    </div>

    <button style="width:6rem"  class="btn btn-lg btn-dark btn-block" type="submit">Make</button>
  </form>
</div>

</template>