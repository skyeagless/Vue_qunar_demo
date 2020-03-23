<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
        <router-link
          tag ="li"
          class="item border-bottom"
          v-for="item of list"
          :key="item.id"
          :to="'/detail/'+ item.id"
        >
          <img class="item-img" :src="item.imgUrl" />
          <div class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.desc}}</p>
            <button class="item-button">查看详情</button>
          </div>
        </router-link>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "HomeRecommend",
    props:{
      list: Array
    }
    // data: function() {
    //   return {
    //     recommendList: [{
    //       id: '001',
    //       imgUrl: "http://img1.qunarzz.com/sight/p0/1909/2c/2c03e6f972b324ea3.img.jpg_200x200_c0a39a89.jpg",
    //       title: "宏村",
    //       desc: "徽派建筑经典",
    //     }, {
    //       id: '002',
    //       imgUrl: "http://img1.qunarzz.com/sight/p0/1908/4e/4e82efecb2e8ade9a3.img.jpg_200x200_92507778.jpg",
    //       title: "西递",
    //       desc: "画里乡村",
    //     }, {
    //       id: '003',
    //       imgUrl: "http://img1.qunarzz.com/sight/p0/1803/68/684c07beee21b37aa3.img.jpg_200x200_5edb4888.jpg",
    //       title: "黄山风景区",
    //       desc: "特别美",
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
    margin-top: .1rem
  .item
    display: flex
    height: 1.9rem
    overflow: hidden
    .item-img
      width: 1.7rem
      height: 1.7rem
      padding: .1rem
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
      .item-button
        line-height: .44rem
        margin-top: .16rem
        background: #ff9300
        padding: .2rem
        border-radius: 0.06rem
        color: white
</style>
