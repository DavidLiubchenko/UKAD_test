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
  font-size: 30px;
  font-family: "Raleway", sans-serif;
  position: relative;
  top: 40px;
  left: 60px;
}
.allProd {
  position: absolute;
  /* border: 2px solid red; */
  margin: 50px;
  width: 95%;
  height: 65%;
}
.prod {
  position: relative;
  display: inline-block;
  border: 4px solid #ebebeb;
  height: 300px;
  width: 400px;
  margin: 10px;
}
.srcImgProd{
  margin: 5px;
  display: block;
  width: auto;
  height: 200px;
  padding-left: 120px;
}
</style>
