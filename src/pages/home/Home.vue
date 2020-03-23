<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>
  </div>

</template>

<script>
  import HomeHeader from './components/Header'
  import HomeSwiper from './components/Swiper'
  import HomeIcons from './components/Icons'
  import HomeRecommend from "./components/Recommend";
  import HomeWeekend from "./components/Weekend"
  import axios from 'axios'
  export default {
    name: 'Home',
    components: {
      HomeHeader,
      HomeSwiper,
      HomeIcons,
      HomeRecommend,
      HomeWeekend,
    },
    data() {
      return {
        lastCity: '',
        swiperList: [],
        iconList: [],
        recommendList:[],
        weekendList:[],
      }
    },
    methods:{
      getHomeInfo: function () {
        axios.get('/api/index.json?city='+ this.$store.state.city).then(this.getHomeInfoSuccess)
      },
      getHomeInfoSuccess: function (res) {
        res =  res.data;
        if(res.ret && res.data){
          this.swiperList = res.data.swiperList;
          this.iconList = res.data.iconList;
          this.recommendList = res.data.recommendList;
          this.weekendList = res.data.weekendList
        }
      }
    },
    mounted() {
      this.lastCity = this.$store.state.city;
      this.getHomeInfo()
    },
    activated() {
      if(this.lastCity !== this.$store.state.city){
        this.lastCity = this.$store.state.city;
        this.getHomeInfo()
      }
    }
  }
</script>

<style>

</style>
