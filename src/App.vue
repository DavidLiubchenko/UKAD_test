<template>
    <nav class="page-navigation">

        <div></div><!-- для отступа -->
        <div><img src="imgs/UCAD.bmp" width="" alt="UCAD"></div>
        <div class="activeNav"><router-link to="/">HOME</router-link></div>
        <div><router-link to="/products">PRODUCTS</router-link></div>

    </nav>
    <router-view/>
</template>

<style>
nav{
    height: 124px;
    background-color: #002B32;
}

router-link {
    color: white; /* Цвет ссылок */
   }
   A:visited {
    color: white; /* Цвет посещенных ссылок */
   }
   A:active {
    color: white; /* Цвет активных ссылок */
   }
.page-navigation div{
    height: 123px;
    display: table-cell;
    width: 150px;
    font-size: large;
    text-align: center;
    vertical-align: middle;
}
.activeNav{
    background-color: #01242b ;
}
</style>