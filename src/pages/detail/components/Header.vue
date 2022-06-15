<template>
  <div>
    <div
      class="header-abs"
      @click="goBack"
      v-show="showAbs"
    >
      <div class="iconfont abs-back-icon">&#xe624;</div>
    </div>
    <div
      class="header-fixed"
      :style="opacityStyle"
      v-show="!showAbs"
    >
      <div class="iconfont fixed-back-icon" @click="goBack">&#xe624;</div>
      景点详情
    </div>
  </div>
</template>
<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    goBack () {
      this.$router.back()
    },
    handleScroll () {
      const top = document.documentElement.scrollTop || document.body.scrollTop || window.pageYOffset
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
@import "~%styles/varibles.styl"
$headerHeight = .86rem
.header-abs
  position absolute
  left .2rem
  top.2rem
  width .8rem
  height .8rem
  border-radius .4rem
  line-height .8rem
  text-align center
  background rgba(0,0,0,.8)
  .abs-back-icon
    color #fff
    font-size .4rem
.header-fixed
  z-index 2
  overflow hidden
  position fixed
  top 0
  left 0
  right 0
  height $headerHeight
  line-height $headerHeight
  text-align center
  color #fff
  background $bgColor
  font-size .32rem
  .fixed-back-icon
    height $headerHeight
    line-height $headerHeight
    position absolute
    top 0
    left 0
    width: .64rem
    text-align: center
    font-size .4rem
</style>
