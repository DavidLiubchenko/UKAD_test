<template>
  <h2>PRODUCTS</h2>
  <div class="allProd">
    <div class="prod" :key="post.id" v-for="post in posts">
      <img class="srcImgProd" :src="post.imgSrc" alt="Здесь невидимая картинка" />
      <h4>{{ post.title }}</h4>
      <h5>{{ post.body }}</h5>
    </div>
  </div>
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
  margin-top: 1%;
  font-size: 30px;
  font-family: "Raleway", sans-serif;
  position: relative;
  top: 40px;
  left: 60px;
}
.allProd {
  position: relative;
  /* border: 2px solid red; */
  margin: 2%;
  width: 95%;
  height: 90%;
}
.prod {
  position: relative;
  display: inline-block;
  border: 4px solid #ebebeb;
  height: 40%;
  width: 20%;
  margin: 1%;
}
.srcImgProd{
  margin: 1%;
  display: block;
  width: auto;
  height: 70%;
  padding-left: 30%;
}
</style>
