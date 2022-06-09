<template>
<div class="icons">
  <swiper :options="swiperOption">
    <swiper-slide v-for="(page, index) in pages" :key="index">
      <div class="icon" v-for="(item, idx) in page" :key="idx">
        <div class="icon-img">
          <img class="icon-img-content" :src = item.imgUrl />
        </div>
        <p class="icon-desc">{{ item.desc }}</p>
      </div>
    </swiper-slide>
  </swiper>

</div>

</template>
<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        if (!pages[Math.floor(index / 8)]) {
          pages.push([])
        }
        pages[Math.floor(index / 8)].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import "~%styles/varibles.styl"
  @import "~%styles/mixins.styl"
  .icons >>> .swiper-container
    overflow hidden
    height 0
    padding-bottom 50%
  .icons
    padding .1rem 0
    .icon
      position relative
      overflow hidden
      float left
      width 25%
      height 0
      padding-bottom 25%
      .icon-img
        position absolute
        top 0
        left 0
        right 0
        bottom .44rem
        box-sizing border-box
        padding 0.1rem
        .icon-img-content
          display block
          margin 0 auto
          height 100%
      .icon-desc
        position absolute
        left 0
        right 0
        bottom 0
        padding 0 10%
        line-height .44rem
        height .44rem
        text-align center
        font-size .2rem
        margin 0
        color $darkTextColor
        ellipse()
</style>
