<template>
  <div id="hmPage">
    <h2 >Home Page</h2>
  </div>
  
  <div id="carusel">
    <button @click="toTheLeft" :class="{ unVisible: position == 0 }">
      <img src="../imgs/left_click.png" alt="leftClickButt" class="arrow prev" />
    </button>
    <div class="allPosts">
      <div
        class="post"
        :key="post.id"
        v-for="post in posts"
        :style="{ left: '-' + position * 33 + '%' }"
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
  <div class="lastLine"></div>
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
    toTheRight() {
      if (this.position < 5) {
        this.position++;
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

    
  },
};
</script>

<style >
  /* @import "./styleHome.css"; */
  @import url("https://fonts.googleapis.com/css2?family=Raleway:wght@800&display=swap");


#hmPage {
  margin-top: 1%;
  font-size: 2.5em;
  font-family: "Raleway", sans-serif;
  position: relative;
  left: 16%;
}

#carusel {
    display: flex;
    position: relative;
    padding: 0;
    margin: 1% 13% 3%;
    height: auto  ;
    overflow: hidden;
    width: 76%;
    /* height: 70%; */
}
.allPosts {
  display:inline-flex;
}
.post {
  box-sizing: border-box;
  position: relative;
  display: inline-block;
  border: 4px solid #ebebeb;
  padding: 0;
  margin: 0 2%;
  min-height: 70%;
  min-width:29%;
}
.srcImg {
  margin: 2% auto;
  padding: 0;
  display: block;
  min-height: 80%;
  width: 71%;
  /* max-width: 100%; */
}
h4,
h5 {
  margin: 2%;
  font-family: "Raleway", sans-serif;
  text-align: center;
  font-size: 0.8em;
}
h4 {
  color: rgb(131, 131, 131);
}
.unVisible {
  visibility: hidden;
}
.prev {
  left: 1%;
}
.next {
  right: 1.6%;
}
.arrow {
  width: 3%;
  z-index: 2;
  position: absolute;
  top: 48%;
  border-radius: 100%;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}


</style>