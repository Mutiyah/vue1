<template>
  <div id="container">

        <h1>{{ name }}</h1>

<div id="sub-container">

    <div id="social">
      <a class="fab fa-instagram " v-bind:href="`https://www.instagram.com/${instagram}`"></a><br />
      <a
        class="fab fa-twitter-square"
        v-bind:href="`https://www.twitter.com/${twitter}`"
      ></a
      ><br />
      <a
        class="fab fa-snapchat-square"
        v-bind:href="`https://www.snapchat.com/add/${snapchat}`"
      ></a>
      <br />
      <a
        class="fas fa-envelope-square"
        v-bind:href="`mailto:${email}`"
      ></a>
    </div>
            <div id="frame">
                  <img src="../assets/images/image.png" alt="Main image">
            </div>
    </div> 
<div id="nav">
<div id="nav-left">
        <a href="#">HOME</a>
        <a href="#">ABOUT</a>
</div>
    <div id="small-image">
        <img src="../assets/images/littleImage.jpg" alt="Little image"  >
    </div>
    <div id="nav-right">
        <a href="#">GALLERY</a>
        <a href="#">CONTACT</a>
</div>
</div>
  </div>
</template>

<script>
// import Vue from 'vue';
import axios from "axios";
// import VueAxios from 'vue-axios'
// Vue.Use(VueAxios,axios)
export default {
  name: "api",
  stopProcess(event) {
    event.preventDefault();
  },
  data() {
    return {
        // img1: 'static/image1.png',
        // img: '',
      values: undefined,
      name: undefined,
      instagram: undefined,
      twitter: undefined,
      email: undefined,
      snapchat: undefined,
    };
  },
  mounted() {
    axios.get(" https://hirng-x2021.glitch.me/api").then((res) => {
      this.values = res.data;
      this.name = this.values.name;
      this.instagram = this.values.social_media.instagram;
      this.twitter = this.values.social_media.twitter;
      this.snapchat = this.values.social_media.snapchat;
      this.email = this.values.social_media.email;
    });
  },
};
</script>

<style scoped>

#container{
    height: 200vh;
    width: 100vw;
    background: linear-gradient(to right, #b30749 0%,#b30749 50%, #c02862 50%, #c02862 100% );
   padding-bottom: 60px;
   position: relative;
    }

#sub-container {
  width: 100vw;
  height: 150vh;
  display: flex;
  flex-direction: row-reverse;
  padding-right: 30px;
}

h1{
  padding-top: 50px;
  text-align: center;
  color: #fff;
}

#frame {
  background-color: #c02862;
  height: 100vh;
  min-width: 50vw;
  margin: auto;
  box-shadow: 0 9px 20px #000;
   overflow-y: hidden;
}
#frame img{
    width: 100%;
    height: 100%;
    overflow-y: hidden;
    }
#social {
  min-width: 50px;
  height: 50vh;
  margin: 50vh 0 50vh 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  margin-left: -65px;
  background-color: transparent;
}

#social a {
  overflow-y: hidden;
  color: #fff;
  font-size: 2.2em;
  text-decoration: none;
}

#small-image{
    background-color: #000 ;
    max-width: 8vw;
    height: 20vh;
    border-radius: 100%;
    overflow-y: hidden;
     margin-left: 2em;
      margin-right: 2em;
        /* padding-right: 4em; */
    }

    #small-image img{
        width: 100%;
        height: 100%;
         border-radius: 100%;
        }
    #nav{
      width: 100vw;
      height: fit-content;
      margin: auto;
        display: flex;
        justify-content: center;
        align-content: center;
        padding-left: 2em;
        padding-right: 2em;
        /* padding-right: 5em; */
    }
        #nav-left{
          margin-top: 8vh;
        /* padding-right: 5px; */
        /* min-width: 30vw; */
        }
    #nav-right{
      /* padding-left: 30px; */
      margin-top: 8vh;
        /* min-width: 30vw; */

    }
        #nav-left a, #nav-right a{
           padding-right: 4em;
           font-size: 1em;
          color: #fff;
          text-decoration: none;
          align-self: flex-end;
          justify-self: flex-end;
        }

        @media screen and (max-width: 600px){
        #frame{
           display: flex;
           flex: 1 1 auto;
           width: 30vw;
           max-width: 160px;
           height: 100vh;
        }
           #nav-left a, #nav-right a{
              padding-right: 1.2em;
              font-size: .9em;
           }

        } 
           @media screen and (max-width: 410px){
             #nav{
               width:100%;
             }
        
           #nav-left a, #nav-right a{
              padding-right: .8em;
              font-size: .6em;
           }
#small-image{
  height: 18vh;
  min-width: 14vw;
   margin-left: .8em;
      margin-right: .8em;
}
        } 
        /* @media screen and (max-width: 600px){
        #nav{
          width: 80vw;
        } */
         /* #nav-left a, #nav-right a{
              padding-right: 1em;
           } */
        /* } */ 
</style>
