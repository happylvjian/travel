<template>
  <div class="header">
    <div class="iconfont back-icon" @click="goBack">&#xe624;</div>
      城市选择
  </div>
</template>
<script>
export default {
  name: 'City',
  data () {
    return {
    }
  },
  methods: {
    goBack () {
      this.$router.back()
    }
  }
}
</script>
<style lang="stylus" scoped>
@import "~%styles/varibles.styl"
$headerHeight = .86rem
.header
  overflow hidden
  position relative
  height $headerHeight
  line-height $headerHeight
  text-align center
  color #fff
  background $bgColor
  font-size .32rem
  .back-icon
    height $headerHeight
    line-height $headerHeight
    position absolute
    top 0
    left 0
    width: .64rem
    text-align: center
    font-size .4rem
</style>
