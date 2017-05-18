<template>
  <nav class="nav" :style="{backgroundImage:'url('+logo+')',backgroundRepeat:'no-repeat',backgroundPosition:'75px center'}">
    <NavItem
      :options="{
        title:'在线咨询',
        items:[
          {title:'按行业',path:'#'},
          {title:'按业务',path:'#'}]}">
    </NavItem>
    <NavItem
      :options="{
        title:'我们', 
        items:[
          {title:'关于机智',path:'#'},
          {title:'公司动态',path:'#'},
          {title:'联系我们',path:'#'}]}">
    </NavItem>
    <NavItem
      :options="{
        title:'技术', 
        items:[]}">
    </NavItem>
    <NavItem
      :options="{
        title:'案例', 
        items:[
          {title:'按行业',path:'#'},
          {title:'按业务',path:'#'}]}">
    </NavItem>
    <NavItem
      :options="{
        title:'业务', 
        items:[
          {title:'智能地产',path:'#'},
          {title:'智能安防',path:'#'}]}">
    </NavItem>
  </nav>
</template>

<script>
import NavItem from './NavItem'
import logo from '../assets/logowhite.png'

export default {
  components: { NavItem },
  data(){
    return {
      logo: logo
    }
  }
}
</script>

<style scoped>
  .nav{
    position: fixed;
    top: 0;
    width: 100%;
    padding-left: 75px;
    padding-right: 75px;
    height: 100px;
    box-sizing: border-box;
    z-index: 100;
    
  }
</style>