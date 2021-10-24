<template>
    <nav class="page-navigation">

        <div></div><!-- для отступа -->
        <div><img src="./imgs/UCAD.png" alt="UKAD" width="100px"></div>
        <div  class="link" @click="vis_firstDiv = true ; vis_secDiv = false"  :class="vis_firstDiv ? 'backColor_Dark':''" ><router-link to="/">HOME</router-link></div><!--class="activeNav" -->
        <div class="link" @click="vis_secDiv = true; vis_firstDiv = false"  :class="vis_secDiv ? 'backColor_Dark':''"><router-link to="/products">PRODUCTS</router-link></div>

    </nav>
    <router-view/>
</template>

<script>
    
    import imgUKAD from './imgs/UCAD.png';
    
    export default {
        data() {
            return {
                vis_firstDiv: true,
                vis_secDiv: false,
            }
        },
        components :{
            imgUKAD
        },

    }

</script>


<style>
*{
	padding: 0;
	margin: 0;
	border: 0;
}
*,*:before,*:after{
	-moz-box-sizing: border-box;
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
}
:focus,:active{outline: none;}
a:focus,a:active{outline: none;}

nav,footer,header,aside{display: block;}

html,body{
	height: 100%;
	width: 100%;
	font-size: 100%;
	line-height: 1;
	font-size: 14px;
	-ms-text-size-adjust: 100%;
	-moz-text-size-adjust: 100%;
	-webkit-text-size-adjust: 100%;
}
input,button,textarea{font-family:inherit;}

input::-ms-clear{display: none;}
button{cursor: pointer;}
button::-moz-focus-inner {padding:0;border:0;}
a, a:visited{text-decoration: none;}
a:hover{text-decoration: none;}
ul li{list-style: none;}
img{vertical-align: top;}

h1,h2,h3,h4,h5,h6{font-size:inherit;font-weight: 400;}

nav{
    height: 124px;
    background-color: #002B32;
    
}

  A {
    color: white; /* Цвет ссылок */
   }
   A:visited {
    color: white; 
   }
   A:active {
    color: white;
    background-color: #01242b; 
   } 


.page-navigation div{
    height: 123px;
    display: table-cell;
    width: 150px;
    font-size: large;
    text-align: center;
    vertical-align: middle;
}
img{
    width: 150px;
    position: relative;
}
.backColor_Dark{
    background-color: #01242b
}

</style>

