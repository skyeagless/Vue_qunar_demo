<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) of pages" :key="index">
        <div
          class="icon"
          v-for="item of page"
          :key="item.id"
        >
          <div class="icon-img">
            <img class='icon-img-content' :src="item.imgUrl">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeIcons',
    props:{
      list: Array
    },
    data: function () {
      return {
        swiperOption: {
          autoplay: false
        }

        // iconList:[{
        //   id: '0001',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
        //   desc: "景点门票"
        // },{
        //   id: '0002',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/97/02f5043b51b2102.png',
        //   desc: "黄山风景区"
        // },{
        //   id: '0003',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/97/02f5043b51b2102.png',
        //   desc: "高铁游"
        // },{
        //   id: '0004',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/90/59a2f523ee2f9202.png',
        //   desc: "西递宏村"
        // },{
        //   id: '0005',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
        //   desc: "一日游"
        // },{
        //   id: '0006',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
        //   desc: "塔川赏秋"
        // },{
        //   id: '0007',
        //   imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/d26d9f5305257233873d029ae5c40967.png',
        //   desc: "黄山翡翠谷"
        // },{
        //   id: '0008',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/87/20656da0ac042002.png',
        //   desc: "齐云山"
        // },{
        //   id: '0009',
        //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
        //   desc: "木坑竹海"
        // },
        // ]
      }
    },
    computed: {
      pages: function () {
        const pages = [];
        this.list.forEach((item,index)=>{
          const page = Math.floor(index / 8);
          if(!pages[page]){
            pages[page] = []
          }
          pages[page].push(item)
        });
        return pages;
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .icons >>> .swiper-container
    height: 0
    padding-bottom: 50%;
  .icon
    position: relative
    overflow: hidden
    width: 25%
    height: 0
    float: left
    padding-bottom: 25%

    .icon-img
      position: absolute
      top: 0
      left: 0
      right: 0
      bottom: .44rem
      box-sizing: border-box
      padding: .1rem
      .icon-img-content
        display: block
        margin: 0 auto
        height: 100%
    .icon-desc
      position: absolute
      left: 0
      right: 0
      bottom: 0
      height: .44rem
      line-height: .44rem
      color: $darkTextColor;
      text-align: center
      ellipsis()
</style>
