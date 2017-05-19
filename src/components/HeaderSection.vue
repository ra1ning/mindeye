<template>
	<div>
	  <ul :style="show_nav?'height:180px;transition:all 0.3s':'height:0px;transition:all 0.3s'" class="nav">
	    <li><a href="#">业务</a></li>
	    <li><a href="#">案例</a></li>
	    <li><a href="#">技术</a></li>
	    <li><a href="#">我们</a></li>
	    <li><a href="#">在线咨询</a></li>
	  </ul>
	  <div class="hamburger">
	  	<img class="banner" src="../assets/banner.jpg" />
	  	<img class="logo" src="../assets/logowhite.png" />
	  	<a @click="showNav"></a>
	  </div>
	</div>
  
</template>
<script type="text/javascript">
	var logo = require('../assets/logo.png')
	export default {
		data(){
			return {
        		show_nav: false,
        		logo: logo
			}
		},
    methods:{
      showNav:function(){
        this.show_nav=!this.show_nav
      }
    },
		mount: function(){
			
		}
	}
</script>
<style scoped>
  .hamburger a{
    display: block;
    width: 10%;
    height: 10%;
    position: absolute;
    background: url(../assets/menu.png) no-repeat center center;
    background-size: 40% 40%;
    right: 0;
    top: 0
  }
  .banner{
  	width: 100%
  }
  .hamburger{
  	position: relative;
  	display: block;
  }
  .logo{
  	width: 10%;
  	position: absolute;
  	left: 20px;
  	top: 5%;
  }
  .nav{
    margin: 0;
    padding: 0;
    list-style: none;
    text-align: center;
    overflow: hidden;
    font-size: 20px;
  }
  .nav li{
    height: 35px;
    line-height: 35px;
    background: #243441;
    font-size: 16px;
    border-bottom: solid 1px #666
  }
  a{
    color:#fff;
    text-decoration: none;
    cursor: pointer;
  }
</style>