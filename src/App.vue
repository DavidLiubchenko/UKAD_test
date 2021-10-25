<template>
  <nav class="page-navigation">
    <div></div> <!-- для отступа -->
    <div><img class="UKADimg" src="./imgs/UCAD.png" alt="UKAD" width="100px" /></div>
    <div
      class="link"
      @click="vis_firstDiv = true; vis_secDiv = false;"
      :class="vis_firstDiv ? 'backColor_Dark' : ''"
    >
      <router-link to="/">HOME</router-link>
    </div>
    <!--class="activeNav" -->
    <div
      class="link"
      @click="
        vis_secDiv = true;
        vis_firstDiv = false;
      "
      :class="vis_secDiv ? 'backColor_Dark' : ''"
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
    imgUKAD
  },
  methods: {},
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  border: 0;
}
*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
:focus,
:active {
  outline: none;
}
a:focus,
a:active {
  outline: none;
}

header,
aside {
  display: block;
}

html,
body {
  height: 100%;
  width: 100%;
  font-size: 100%;
  line-height: 1;
  font-size: 14px;
  -ms-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
input,
button,
textarea {
  font-family: inherit;
}

input::-ms-clear {
  display: none;
}
button {
  cursor: pointer;
}
button::-moz-focus-inner {
  padding: 0;
  border: 0;
}
.UKADimg {
  vertical-align: top;
  width: 150px;
  position: relative;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: 400;
}

nav {
  display: block;
  height: 124px;
  background-color: #002b32;
}

A,
A:visited,
A:active,
A:hover {
  color: white;
  background-color: #01242b; /* Цвет ссылок */
  text-decoration: none;
}

.page-navigation div {
  height: 123px;
  display: table-cell;
  width: 150px;
  font-size: large;
  text-align: center;
  vertical-align: middle;
}

.backColor_Dark {
  background-color: #01242b;
}
footer {
  display: block;
  background-color: #01242b;
  width: 100%;
  height: 10%;
  position: absolute;
  bottom: 0;
}
</style>
