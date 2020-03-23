<template>
  <ul class="list" >
    <li class="item" v-for="item of letters"
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchstart.prevent = "handleTouchStart"
        @touchmove = "handleTouchMove"
        @touchend = "handleTouchEnd"
    >{{item}}
    </li>
  </ul>
</template>

<script>
  export default {
    name: 'CityAlphabet',
    props:{
      cities: Object
    },
    computed:{
      letters: function () {
        const letters = [];
        for(let i in this.cities){
          letters.push(i)
        }
        return letters;//['a','b','c']
      }
    },
    data: function() {
      return {
        touchStatus: false,
        startY: 0,
        timer: null
      }
    },
    updated() {
      this.startY = this.$refs['A'][0].offsetTop;
    },
    methods:{
      handleLetterClick: function (e) {
          this.$emit('change', e.target.innerText)
      },
      handleTouchStart: function () {
        this.touchStatus = true;
      },
      handleTouchMove: function (e) {
        if(this.touchStatus){
          const touchY = e.touches[0].clientY - 79;
          const index = Math.floor((touchY-this.startY)/20);
          if(index >= 0 && index < this.letters.length){
            this.$emit('change',this.letters[index])
          }
        }
      },
      handleTouchEnd: function () {
        this.touchStatus = false;
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .list
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    right: 0
    top: 1.58rem
    bottom: 0
    width: .4rem
    .item
      text-align: center
      line-height: .4rem
      color: $bgColor
</style>
