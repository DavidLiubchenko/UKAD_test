<template>
  <div id="hmPage">
    <h2>PRODUCTS</h2>
  </div>

  <template class="centerElem">
    <div class="allProd">
      <div class="prod" :key="post.id" v-for="post in posts">
        <img class="srcImgProd" :src="post.imgSrc" alt="Здесь невидимая картинка" />
        <h4>{{ post.title }}</h4>
        <h5>{{ post.body }}</h5>
      </div>
    </div>
  </template>
  <div class="lastLine"></div>
</template>

<script>
export default {
  created() {
    const postsLocData = localStorage.getItem("UKAD_posts_movies");
    if (postsLocData) {
      this.posts = JSON.parse(postsLocData);
    }
  },
  data() {
    return {
      posts: [],
    };
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@800&display=swap");

h2 {
  display: flex;
  margin-top: 2%;
  font-size: 30px;
  font-family: "Raleway", sans-serif;
  position: relative;
  left: 2%;
}
h4,
h5 {
  margin-top: 2%;
  font-size: calc(0.5em + 0.5vw);
}
.allProd {
  display: flex;
  flex-wrap: wrap;
  width: 76%;
  justify-content: center;
}
.prod {
  position: relative;
  border: 4px solid #ebebeb;
  width: 20%;
  margin: 1%;
  overflow: hidden;
  font-size: 0.8em;
}
.srcImgProd {
  display: flex;
  margin: 2% auto;
  height: 70%;
  width: auto;
  max-width: 60%;
}
</style>
