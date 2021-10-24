<template>
  <h2>Home Page</h2>
  <div id="carousel" class="carousel">
    <button @click="toTheLeft" class="arrow prev">⇦</button>
    <ul>
      <div class="post" :v-for="post in posts"> 
        <li>
          <h4>Имя поста {{post.title}}</h4>
          <div> <img :src="post.img" alt="Типа картинка тут"></div>
          <h5>Описание поста {{post.body}}</h5>
        </li>
      </div>
    </ul>
    
    <button @click="toTheRight" class="arrow next">⇨</button>
  </div>
</template>

<script>

  export default {
    data() {
      return {
        posts: [

          {id:1, title:'один', img:'', body:'Описание чего-то 1'},
          {id:2, title:'два', img:'', body:'Описание чего-то 2'},
          {id:3, title:'три', img:'', body:'Описание чего-то 3'},
          {id:4, title:'четыре', img:'', body:'Описание чего-то 4'},
          {id:5, title:'пять', img:'', body:'Описание чего-то 5'},
          {id:6, title:'шесть', img:'', body:'Описание чего-то 6'},
          {id:7, title:'семь', img:'', body:'Описание чего-то 7'},
          {id:8, title:'восемь', img:'', body:'Описание чего-то 8'},

        ],
        width : 130,
        count : 3,
        list : carousel.querySelector('ul'),
        listElems : carousel.querySelectorAll('li'),
        position : 0,
        }
    },
    methods: {
      toTheLeft () {

        this.position += this.width * this.count;
        this.position = Math.min(this.position, 0)
        this.list.style.marginLeft = this.position + 'px';

      },

      toTheRight () {

        this.position -= this.width * this.count;
        this.position = Math.max(this.position, -this.width * (this.listElems.length - this.count));
        this.list.style.marginLeft = this.position + 'px';

      }
    },
  }


    // отметить картинки для удобства разработки



</script>

<style>
.arrow{
  position: block;
}
.post {
  position: relative;
}
</style>