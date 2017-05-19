<template>
<div class="container">
  <NavSection :class="trans"></NavSection>
  <Banner/>
  <HeaderSection class="phone-nav"></HeaderSection>
  <TitleSection titleName="主要业务" class="title"></TitleSection>
  <MainSection></MainSection>
  <TitleSection titleName="关于我们" class="title-desc"></TitleSection>
  <div class="bottom">
    <img :src="bottom">
    <p><span style="font-size18px;color:#9c9c9c">
      MindCar最初由汽车行业资深人士为主要成员组成的创始团队，现在已经形成一套以算法、产品、硬件、设计、运营在内的完整体系，团队成员来自于国内外知名院校的毕业生，以及来自知名企业与研究机构。
    </span>
    <br><br>
    <span class="desc-bottom">
      我们致力于通过图像识别、机器学习和人工智能技术，为智慧城市交通，驾驶辅助乃至自动驾驶做出更大的贡献。
    </span>
    <span class="more">了解更多</span>
    </p>
    
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
  components: {  NavSection,HeaderSection,MainSection, Foot, TitleSection, Banner},
  data(){
    return {
      trans: 'noTrans',
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
  }
}
</script>

<style scoped>
  .container{
    box-sizing: border-box;
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
  .title-desc{
     margin:116px auto 60px
  }

  .bottom{
    margin: 0 auto;
    overflow: hidden;
  }

  .bottom img{
    width: 574px;
    margin-right: 90px;
  }
  .bottom>*{
    float: left;
    display: block;
  }

  .more{
    width: 130px;
    height: 48px;
    line-height: 48px;
    border: solid 2px #00a0ea;
    display: block;
    text-align: center;
    margin-top: 24px;
  }

  p{
    line-height: 32px;
    width: 590px;
    font-size: 18px;
    text-align: left;
  }
  
  .desc-bottom{
    height: 82px;
    border-left: 10px solid #00a9ea;
    display: block;
    background-color: #f8f8f8;
    padding: 10px;
    box-sizing: border-box;
  }
  .phone-nav{
      display: none;
  }

/*大于1280px;单排定宽居中*/
  @media screen and (min-width: 1280px) {
    .bottom{
      width: 1280px;
      margin: 0 auto;
      overflow: hidden;
      margin-bottom: 144px;
    }
  }

/*小于1280,大于920单排自适应*/
  @media screen and (max-width: 1280px) and (min-width: 920px){
    .bottom{
      width: 90%;
      margin: 0 auto;
      overflow: hidden;
      margin-bottom: 144px;
    }
    .bottom>p,.bottom>img{
      font-size: 14px;
      width: 40%;
      margin-top: 0;
      line-height: 26px;
    }
    .bottom>img{
      margin-right: 20px;
      width: 56%;
    }
    .desc-bottom{
      height: auto!important;
    }
  }

  /*小于920px,隐藏手机导航栏,双排自适应*/
  @media screen and (max-width: 920px) {
    .trans,.noTrans{
      display: none!important;
    }
    .title,.title-desc{
      margin: 30px auto 30px;;
    }
    .phone-nav{
      display: block;
    }
    .bottom>*{
      float: none;
      margin:10px auto!important;
      width: 90%!important;
      box-sizing: border-box;
      font-size: 14px;
      line-height: 22px;
    }
    .bottom{
      width: 100%;
      overflow: hidden;
      margin-bottom: 40px;
    }
    .desc-bottom{
      height: auto!important;
    }
  }


</style>