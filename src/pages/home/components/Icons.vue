<template>
<div class="icons">
  <swiper>
    <swiper-slide v-for="(page, index) in pages" :key="index">
      <div class="icon" v-for="(item, idx) in page" :key="idx">
        <div class="icon-img">
          <img class="icon-img-content" :src = item.iconUrl />
        </div>
        <p class="icon-desc">{{ item.iconDesc }}</p>
      </div>
    </swiper-slide>
  </swiper>

</div>

</template>
<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      iconList: [
        {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点热门景点热门景点热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }, {
          iconUrl: 'http://img1.qunarzz.com/piao/fusion/1611/54/ace00878a52d9702.png',
          iconDesc: '热门景点'
        }
      ]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
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
    margin-top .1rem
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
