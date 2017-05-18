<template>
<div class="container">
  <Banner/>
  <NavSection :class="trans"></NavSection>
  <HeaderSection></HeaderSection>
  <TitleSection titleName="主要业务" class="title"></TitleSection>
  <MainSection></MainSection>
  <TitleSection titleName="关于我们" class="title-desc"></TitleSection>
  <div class="bottom">
    <img :src="bottom">
    <p><span style="font-size18px;color:#9c9c9c">
      MindCar最初由汽车行业资深人士为主要成员组成的创始团队，现在已经形成一套以算法、产品、硬件、设计、运营在内的完整体系，<br>团队成员来自于国内外知名院校的毕业生，以及来自知名企业与研究机构。
    </span>
    <br><br>
    <br><br>
    <span class="desc-bottom">
      我们致力于通过图像识别、机器学习和人工智能技术，为智慧城市交通，驾驶辅助乃至自动驾驶做出更大的贡献。
    </span>
    </p>
    <button>了解更多</button>
  </div>
  
  <Foot></Foot>
</div>
</template>

<script>
import MainSection from './MainSection'
import NavSection from './NavSection'
import TitleSection from './TitleSection'
import Foot from './Foot'
import bottom from '../assets/bottom.png'
import Banner from './Banner'
import HeaderSection from './HeaderSection'
export default {
  components: {  NavSection,HeaderSection,MainSection, Foot, TitleSection, Banner },
  data(){
    return {
      trans: 'noTrans',
      // banner: banner,
      bottom: bottom
    }
  },
  methods:{
    handleScroll:function(){
      if(window.scrollY>=200){
        this.trans='trans'
      }else{
        this.trans='noTrans'
      }
    }
  },
  beforeMount(){
    window.addEventListener('scroll', this.handleScroll);
    console.log(this.bottom)
  }
}
</script>

<style scoped>
  .container{
    width: 100%;
    box-sizing: border-box;
  }
  img{
    width: 100%;
  }
  .trans{
    background-color: rgba(0,0,0,1);
    transition: all 0.5s;
  }
  .noTrans{
    background-color: rgba(0,0,0,0);
    transition: all 0.5s;
  }
  .title{
    margin: 90px auto 84px;
  }
  p{
    text-align: center;
    line-height: 32px;
    max-width: 584px;
    min-width: 480px;
    font-size: 18px;
    text-align: left;
  }
  .title-desc{
     margin:116px auto 60px
  }
  .bottom{
    width: 1250px;
    margin: 0 auto;
    overflow: hidden;
    margin-bottom: 144px;
  }

  .bottom img{
    max-width: 574px;
    min-width: 480px;
    max-height: 383px;
    margin-right: 90px;
  }
  .bottom>*{
    float: left;
  }
  .desc-bottom{
    height: 82px;
    border-left: 10px solid #00a9ea;
    display: block;
    background-color: #f8f8f8;
    padding: 10px;
    box-sizing: border-box;
  }

  @media screen and (max-width: 800px) {
    .bottom>*{
      float: none;
      display: block;
      margin-left: auto!important;
      margin-right: auto!important;
      padding:20px;
    }
    .bottom{
      width: auto!important;
      margin: 0 auto;
      overflow: hidden;
      margin-bottom: 144px;
    }
    .right{
      float: left!important;
    }
  }
</style>