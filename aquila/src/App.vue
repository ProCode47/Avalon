<template>
<div class="app">
  <h1>{{mainName}}</h1>
  <!-- Main Hero for Page -->
<img class="hero" src="./assets/hero.png">

<!-- Navigation  -->
<div class="nav"> 
  <a href="##"> HOME </a>
   <a href="#"> ABOUT </a>
   <div class="crop">
<img src="./assets/actionvance-m2h5-H_08Qk-unsplash.jpg">
  </div>
    <a class="gallery" href="#">  GALLERY </a>
     <a href="#"> CONTACT </a>
</div>

<!-- Social Bar  -->
<div class="social">
 <a v-bind:href="`https://instagram.com/${instagram}`"><span class="fa fa-instagram"></span> </a> 
 <a v-bind:href="`https://twitter.com/${twitter}`"> <span class="fa fa-twitter"></span> </a> 
  <a v-bind:href="`https://snapchat.com/${snapchat}`"> <span class="fa fa-snapchat"></span> </a>
   <a v-bind:href="`https://${email}`"><span class="fa fa-envelope"></span> </a>
</div>


</div>
</template>

<script>
import axios from "axios";
import './style.css'
export default {
  name: "App",

  // State and Component Data
  data() {
    return {
      mainName: "",
      twitter:"",
      instagram:"",
      snapchat:"",
      email:""
    };
  },

  // Cycle Methods
  created (){
    axios
        .get(
          "https://hirng-x2021.glitch.me/api"
        )
        .then((res) => {
          this.mainName = res.data.name;
          this.twitter = res.data.social_media.twitter;
          this.instagram = res.data.social_media.instagram;
          this.snapchat = res.data.social_media.snapchat;
          this.email = res.data.social_media.email;
        });
  },
 
};
</script>
