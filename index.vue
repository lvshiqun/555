<template>
<div class="app">
  <div class="header">                                                                                   
    <img @click="fen"  class="fen" src="/img/san.png" alt="">
    <img class="biao"   src="/img/tou.png" alt="">
  <img @click="cha" class="cha"  src="/img/cha.png" alt="">
  </div>

<van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
  <van-swipe-item v-for="(img ,index) in imgs" :key="index" ><img v-lazy="img" alt=""></van-swipe-item>
</van-swipe>
<van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
  <van-swipe-item v-for="(item,index) in items" :key="index" ><img v-lazy="item.imgs" alt=""></van-swipe-item>
</van-swipe>
<div class="xt">
<img src="img/TB1vMMwChTpK1RjSZFMXXbG_VXa-1125-30.png" alt="">
</div>

<van-grid  :border="false" :column-num="4">
  <van-grid-item  @click="jump" v-for="(ico ,i) in icons" :key="i">
    <router-link :to="`/article/${i}`">
    <img v-lazy="ico.im" alt="">
    <div class="text">{{ico.text}}</div>
    </router-link>
  </van-grid-item>
</van-grid>
<div>
  <img src="img/download38.png" alt="">
</div>
<van-grid  :border="false" :column-num="2">
  <van-grid-item v-for="(ico ,i) in icons" :key="i">
<img v-lazy="ico.im1" alt="">
<span>{{ico.title}}</span>
<p>
   ￥{{ico.price}}
  <img src="img/buyicon.gif" alt="">
 </p>
  </van-grid-item>title:'sadsa',
</van-grid>

<van-tabbar v-model="active">
  <van-tabbar-item >
    <span>首页</span>
    <img slot="icon" v-lazy="'img/home1.png'">
  </van-tabbar-item>
   <van-tabbar-item @click="shopping2">
    <span>购物车</span>
    <img slot="icon" v-lazy="'img/shopping.png'">
  </van-tabbar-item>
   <van-tabbar-item @click="shopping1">
    <span>分类</span>
    <img slot="icon" v-lazy="'img/lei1.png'">
  </van-tabbar-item>
   <van-tabbar-item>
    <span>客服</span>
    <img slot="icon" v-lazy="'img/phone.png'">
  </van-tabbar-item>
   <van-tabbar-item @click="login">
    <span>我的</span>
    <img slot="icon" v-lazy="'img/me.png'">
  </van-tabbar-item>
</van-tabbar>
</div>
</template>
<script>
export default {
  data() {
    return {
       active: 0,
      imgs:[
        'img/u=3032142929,1948042204&fm=15&gp=0.jpg',
        'img/timg.jpg',
        'img/u=1442806348,3227135484&fm=26&gp=0.jpg',
        'img/u=1593340586,3528490980&fm=15&gp=0.jpg',
      ],price:'66',
      icons:[
        {price:'266',title:'执着',im1:'img/201804185561564420.jpg',im2:'img/download20.png',im:'img/主图.jpg',text:"蛋糕"},
        {price:'300',title:'一生一世',im1:'img/201804184520855253.jpg',im:'img/download1.jpg',text:"鲜花",},
        {price:'299',title:'冬雪初晴',im1:'img/201804187156642546.png',im:'img/download.jpg',text:"花篮"},
        {price:'298',title:'炽热的爱',im1:'img/201804217613186532.jpg',im:'img/download001.jpg',text:"巧克力"},
        {price:'297',title:'一生岁月',im1:'img/ceng_xh.jpg',im:'img/download002.jpg',text:"果篮"},
        {price:'299',title:'一生陪伴',im1:'img/download1.jpg',im:'img/download003.jpg',text:"公仔"},
        {price:'277',title:'深情挚爱',im1:'img/download003.jpg',im:'img/download004.jpg',text:"绿色植物"},
        {price:'355',title:'花月飘香',im1:'img/download005.jpg',im:'img/download005.jpg',text:"月饼"},
    
      ]
     
      
    }


  },
  methods:{
     shopping2(){
     this.$router.push('/shopping2')
    },
    index(){
       this.$router.push('/index')
    },
    shopping1(){
     this.$router.push('/shopping1')
    },
    jump(){
    
    },
    login(){
       this.$router.push('/login')
    },
    cha(){
        this.$router.push('/search')
    },
    fen(){
        this.$router.push('/fenlei')
    }
  },
  mounted(){
   this.axios.get('/index').then(res=>{
     console.log(res.data.results);
     let results=res.data.results
     this.items=results
     console.log(results)
      // items.forEach( items=>{
      //         if( items.imgs != null){
      //            items.imgs = require('img'+  items.imgs);
      //         }
      //         this. items.push( items);
      //     });
      //     // 修改状态
  
   })
  }

};
</script>

<style scoped>
.header{
  height: 38.5px;
  background-color:  #4cb19f;
  position: relative;;
}

.fen{
  position: absolute;
  width: 8%;
  top: 23%;
}
.cha{
  position: absolute;
  width: 6%;
  top: 15%;
  right: 20px;
}
.biao{
  position: absolute;
width: 30%;
left:35%;
}
.app{
  position: relative;
  margin-bottom: 20px;
}
.my-swipe img{
  width:100%;
}
.my-swipe .van-swipe-item {
  color: #fff;
  font-size: 20px;
  line-height: 150px;
  text-align: center;
  background-color: #39a9ed;
}
img{
  width: 100%;
}
.my-swipe{
  height: 120px;
}
.xt{
  position: relative;
  margin-top: -11px;
}
.text{
  font-size: 10px;
  text-align: center;
}
</style>