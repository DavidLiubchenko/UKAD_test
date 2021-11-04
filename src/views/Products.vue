<template>
  <h2>PRODUCTS</h2>
  <div class="allProd">
    <div class="prod" :key="post.id" v-for="post in posts">
      <img class="srcImgProd" :src="post.imgSrc" alt="Здесь невидимая картинка" />
      <h4>{{ post.title }}</h4>
      <h5>{{ post.body }}</h5>
    </div>
  </div>
  <div class="lastLine"></div>
</template>

<script>

export default {
  created(){
    const postsLocData = localStorage.getItem("UKAD_posts_movies");
    if(postsLocData){
      this.posts = JSON.parse(postsLocData);
    }
  },
  data() {
    return {
      posts:[],
    };
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@800&display=swap");

h2 {
  margin-top: 3%;
  font-size: 30px;
  font-family: "Raleway", sans-serif;
  position: relative;
  left: 6%;
}
h4,h5{
  margin-top: 2%;
  font-size: 0.9em;
}
.allProd {
  display: inline-flex;
  flex-wrap: wrap;
  margin: 1% 5% 1% 5%;
  width: 80%;
  min-height: 15%;
  max-height: 20%;
  height: 20%;
}
.prod {
  position: relative;
  border: 4px solid #ebebeb;
  height: 43%;
  width: 20%;
  margin: 1%;
  overflow: hidden;
}
.srcImgProd{
  display: block;
  margin: auto;
  height: 70%;
  max-width: 100%;
}
</style>
