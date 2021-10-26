<template>
  <h2>Home Page</h2>
  <div id="carusel" >
    <button
      @click="toTheLeft"
      class="arrow prev"
      :class="position == 0 ? 'unVisible' : ''"
      
    >
      &#8249;
    </button>
  <div class="allPosts">
    <div class="post" :key="post.id" v-for="post in posts" :style="{'left':'-'+(position*308)+'px'}">
      
        <img class="srcImg" :src="post.imgSrc" alt="Здесь невидимая картинка">
        <h4>{{ post.title }}{{ position }}</h4>
        <h5>{{ post.body }} {{ massPosition }}</h5>
      
    </div>
  </div>

    <button
      @click="toTheRight"
      class="arrow next"
      :class="position == 5 ? 'unVisible' : ''"
    >
      &#8250;
    </button>
  </div>
</template>

<script>

export default {
  
  data() {
    return {
      position: 0,
      posts: [
        { id: 1, title: "один", imgSrc: "", body: "Описание чего-то 1" },
        { id: 2, title: "два", imgSrc: "", body: "Описание чего-то 2" },
        { id: 3, title: "три", imgSrc: "", body: "Описание чего-то 3" },
        { id: 4, title: "четыре", imgSrc: "", body: "Описание чего-то 4" },
        { id: 5, title: "пять", imgSrc: "", body: "Описание чего-то 5" },
        { id: 6, title: "шесть", imgSrc: "", body: "Описание чего-то 6" },
        { id: 7, title: "семь", imgSrc: "", body: "Описание чего-то 7" },
        { id: 8, title: "восемь", imgSrc: "", body: "Описание чего-то 8" },
      ],
    };
  },

  methods: {
    toTheLeft() {
      if (this.position > 0) {
        this.position--;
      }
    },

    toTheRight() {
      if (this.position < 5) {
        this.position++;
      }
    },
  },
};
</script>

<style>
.allPosts{
  width: 9999px;
  margin: 10px;
  padding: 20px;
  border: 2px solid red;
  height: 440px;
}
.unVisible {
  visibility: hidden;
}
#carusel {
  position: relative;
  border: 2px solid rgb(18, 15, 228);
  padding: 20px 90px;
  margin: 100px 15%;
  height: 500px;
  width: 1240px;
  overflow: hidden;
}

.arrow {
  z-index: 1;
  position: absolute;
  top: 45%;
  padding: 0;
  background: white;
  border-radius: 30px;
  font-size: 24px;
  line-height: 24px;
  color: #444;
  display: table-cell;
  width: 40px;
  height: 40px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
.prev {
  left: 95px;
}

.next {
  right: 105px;
}

.post {
  position: relative;
  display: inline-block;
  border: 4px solid #ebebeb;
  margin: 20px;
  height: 440px;
}
.srcImg {
  border: 2px solid yellowgreen;
  display: block;
  width: 300px;
  height: 300px;
}
</style>
