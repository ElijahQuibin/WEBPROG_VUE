<script></script>

<template>
    <ul>
      <li v-for="instrument in instruments" :key="instrument.id">{{ instrument.name }}</li>
    </ul>
    
  <h1>Food</h1> 
  <personal-profile/> <br>
  <food-item/> <br>
  <food-item2/> <br>
  <food-item/> <br>
  <food-item2/> <br>
</template>

<style></style>
