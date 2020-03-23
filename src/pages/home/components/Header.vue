<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{ this.$store.state.city }}
        <span class="iconfont arrow-icon">&#xe62d;</span>
      </div>
    </router-link>

  </div>

</template>

<script>
  export default {
    name: 'HomeHeader'
  }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header
    display: flex
    line-height: $headerHeight
    background: $bgColor
    color: #fff
    .header-left
      width: .64rem
      float: left
      .back-icon
        text-align: center
        font-size: .4rem
    .header-input
      flex: 1
      height: 0.64rem
      line-height: 0.64rem
      margin-top: 0.12rem
      margin-left: 0.2rem
      padding-left: .2rem
      background: #ffffff
      border-radius: 0.1rem
      color: #ccc
    .header-right
      min-width: 1.04rem
      padding: 0 .1rem
      float: right
      text-align: center
      color: white
      .arrow-icon
        font-size: .24rem
</style>

