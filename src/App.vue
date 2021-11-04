<template>
  <nav class="page-navigation">
    <div></div>
    <div><img class="UKADimg" src="./imgs/UCAD.png" alt="UKAD" /></div>
    <div
      class="link"
      @click="
        vis_firstDiv = true;
        vis_secDiv = false;
      "
    >
      <router-link to="/" class="router" :class="{ backColor_Dark: vis_firstDiv }"
        >HOME</router-link
      >
    </div>
    <div
      class="link"
      @click="
        vis_secDiv = true;
        vis_firstDiv = false;
      "
    >
      <router-link
        to="/products"
        tag="button"
        class="router"
        :class="{ backColor_Dark: vis_secDiv }"
        >PRODUCTS</router-link
      >
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

<style scoped>
@import "./App_css.css";
</style>
