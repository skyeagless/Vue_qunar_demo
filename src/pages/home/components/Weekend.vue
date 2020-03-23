<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom"
          v-for="item of list"
          :key="item.id"
      >
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.imgUrl" />
        </div>

        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "HomeWeekend",
    props:{
      list: Array
    }
    // data: function() {
    //   return {
    //     recommendList: [{
    //       id: '001',
    //       imgUrl: "http://img1.qunarzz.com/sight/source/1505/7e/a5ec29839a2a9e.jpg_r_640x214_53b4f72d.jpg",
    //       title: "黄山必打卡",
    //       desc: "清泉，烟幕，轻舟",
    //     }, {
    //       id: '002',
    //       imgUrl: "http://img1.qunarzz.com/sight/source/1507/9d/72ff8b13969768.jpg_r_640x214_80736a67.jpg",
    //       title: "当地人爱逛",
    //       desc: "温泉，乐园，演出，样样有",
    //     }, {
    //       id: '003',
    //       imgUrl: "http://img1.qunarzz.com/sight/source/1811/32/c7d92997188d64.jpg_r_640x214_ba3164a5.jpg",
    //       title: "品黄山古韵",
    //       desc: "品黄山古迹神韵，感受黄山文化",
    //     },]
    //   }
    // }
  }
</script>

<style lang="stylus" scoped>
  @import "~styles/mixins.styl"
  .recommend-title
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item-img-wrapper
    overflow: hidden
    height: 0
    padding-bottom: 37.2%
    .item-img
      width: 100%
  .item-info
    flex: 1
    padding: .1rem
    min-width: 0
    .item-title
      line-height: .54rem
      font-size: .32rem
      ellipsis()
    .item-desc
      line-height: .4rem
      color: #ccc
      ellipsis()

</style>
