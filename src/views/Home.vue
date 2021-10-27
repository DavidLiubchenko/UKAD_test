<template>
  <h2 id="hmPage">Home Page</h2>
  <div id="carusel">
    <button @click="toTheLeft" class="arrow prev" :class="{ unVisible: position == 0 }">
      &#8249;
    </button>
    <div class="allPosts">
      <div
        class="post"
        :key="post.id"
        v-for="post in posts"
        :style="{ left: '-' + position * 360 + 'px' }"
      >
        <img class="srcImg" :src="post.imgSrc" alt="Здесь невидимая картинка" />
        <h4>{{ post.title }}</h4>
        <h5>{{ post.body }}</h5>
      </div>
    </div>

    <button v-if="position != 5" @click="toTheRight" class="arrow next">&#8250;</button>
  </div>
</template>

<script>
export default {
  created() {
    this.getMovie(this.API_URL);
  },
  data() {
    return {
      API_KEY: "a73fcdbb-f7fc-4ffe-8dfc-59f85ad6dece",
      API_URL: "https://kinopoiskapiunofficial.tech/api/v2.2/films/top",
      position: 0,
      posts: [],
    };
  },

  methods: {
    toTheLeft() {
      if (this.position > 0) {
        this.position--;
      }
    },
    async getMovie(url) {
      const resp = await fetch(url, {
        headers: {
          "Content-Type": "application/json",
          "X-API-KEY": this.API_KEY,
        },
      });
      const respData = await resp.json();
      this.createPosts(respData);
    },

    createPosts(Data) {
      //console.log(Data.films[0].nameEn)
      for (let i = 0; i < 8; i++) {
        const NewPost = {
          id: i,
          title: Data.films[i].nameEn,
          imgSrc: Data.films[i].posterUrl,
          body: "Year: "+Data.films[i].year+", Rating: "+Data.films[i].rating+", Country: "+Data.films[i].countries[0].country,
        };
        this.posts.push(NewPost);
      }
      localStorage.setItem("UKAD_posts_movies", JSON.stringify(this.posts));
    },

    toTheRight() {
      if (this.position < 5) {
        this.position++;
      }
    },
  },
};
</script>

<style scoped>
@import "./styleHome.css";
</style>
