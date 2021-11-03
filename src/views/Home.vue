<template>
  <h2 id="hmPage">Home Page</h2>
  <div id="carusel">
    <button @click="toTheLeft" :class="{ unVisible: position == 0 }">
      <img src="../imgs/left_click.png" alt="leftClickButt" class="arrow prev" />
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

    <button v-if="position != 5" @click="toTheRight">
      <img src="../imgs/right_click.png" alt="RightClickButt" class="arrow next" />
    </button>
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
          body:
            "Year: " +
            Data.films[i].year +
            ", Rating: " +
            Data.films[i].rating +
            ", Country: " +
            Data.films[i].countries[0].country,
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
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@800&display=swap");

h4,
h5 {
  margin: 15px;
  font-family: "Raleway", sans-serif;
  text-align: center;
}
h4 {
  color: rgb(131, 131, 131);
}
#hmPage {
  margin-top: 0;
  font-size: 30px;
  font-family: "Raleway", sans-serif;
  position: relative;
  top: 8%;
  left: 17.5%;
}

#carusel {
  position: relative;
  padding: 20px;
  margin: 100px 15%;
  height: 500px;
  width: 1100px;
  overflow: hidden;
}
.allPosts {
  width: 9999px;
  height: 440px;
}
.post {
  position: relative;
  display: inline-block;
  border: 4px solid #ebebeb;
  margin: 0 20px;
  height: 440px;
  width: 320px;
}
.srcImg {
  margin: 5px;
  display: block;
  width: auto;
  height: 350px;
  text-align: center;
  padding-left: 35px;
  margin-bottom: 20px;
}
.unVisible {
  visibility: hidden;
}
.prev {
  left: 20px;
}

.next {
  right: 5px;
}
.arrow {
  z-index: 1;
  position: absolute;
  top: 48%;
  padding: 0;
  background: white;
  border-radius: 20px;
  font-size: 24px;
  line-height: 24px;
  color: #444;
  display: table-cell;
  width: 40px;
  height: 40px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
</style>
