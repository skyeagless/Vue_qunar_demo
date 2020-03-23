<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <!-- slides -->
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeSwiper',
    props:{
      list: Array
    },
    data: function () {
      return {
        swiperOption: {
          pagination: ".swiper-pagination",
          loop: true
        }
      }
    },
    computed:{
      showSwiper: function(){
        return this.list.length
      }
    }
        // swiperList:[{
        //   id:'0001',
        //   imgUrl: "//imgs.qunarzz.com/vc/44/e9/86/95bc36c9e1c06ebd68bdfe222e.jpg_92.jpg"
        // },{
        //   id: '0002',
        //   imgUrl: "//imgs.qunarzz.com/vc/6d/9f/35/b8ad5468f73fd60ec0ced086f6.jpg_92.jpg"
        // }]
  }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: white
  .wrapper
    width: 100%
    height: 31.25vw
    .swiper-img
      width: 100%
</style>
