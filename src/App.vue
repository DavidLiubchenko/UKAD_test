<template>
  <nav class="page-navigation">
    <div></div>
    <div><img class="UKADimg" src="./imgs/UCAD.png" alt="UKAD" width="100px" /></div>
    <div
      class="link"
      @click="
        vis_firstDiv = true;
        vis_secDiv = false;
      "
      :class=" {'backColor_Dark' : vis_firstDiv}"
    >
      <router-link to="/">HOME</router-link>
    </div>
    <div
      class="link"
      @click="
        vis_secDiv = true;
        vis_firstDiv = false;
      "
      :class="{'backColor_Dark' : vis_secDiv}"
    >
      <router-link to="/products">PRODUCTS</router-link>
    </div>
  </nav>
  <router-view />
</template>

<script>
//import axios from 'axios';
import imgUKAD from "./imgs/UCAD.png";

export default {
  data() {
    return {
      vis_firstDiv: true,
      vis_secDiv: false,
    };
  },
  components: {
    imgUKAD,
  },
  methods: {},
};
</script>

<style>
@import "./App_css.css";
</style>
