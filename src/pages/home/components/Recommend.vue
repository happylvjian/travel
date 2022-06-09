<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item in recommendedList " :key="item.id">
        <img class="item-img" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-btn">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      recommendedList: [
        {
          id: '0001',
          imgUrl: 'https://tr-osdcp.qunarzz.com/tr-osd-tr-space/img/45a4e09567253f0051fa23c0ea9215d1.jpg_640x480x70_65b36d72.jpg',
          title: '大连圣亚海洋世界',
          desc: '浪漫大连首站，狼浪漫的海洋主题乐园'
        },
        {
          id: '0002',
          imgUrl: 'https://tr-osdcp.qunarzz.com/tr-osd-tr-space/img/45a4e09567253f0051fa23c0ea9215d1.jpg_640x480x70_65b36d72.jpg',
          title: '大连圣亚海洋世界',
          desc: '浪漫大连首站，狼浪漫的海洋主题乐园'
        },
        {
          id: '0003',
          imgUrl: 'https://tr-osdcp.qunarzz.com/tr-osd-tr-space/img/45a4e09567253f0051fa23c0ea9215d1.jpg_640x480x70_65b36d72.jpg',
          title: '大连圣亚海洋世界',
          desc: '浪漫大连首站，狼浪漫的海洋主题乐园'
        }
      ]
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import "~%styles/mixins.styl"
  .title
    margin-top .1rem
    line-height .8rem
    font-size .32rem
    background #eee
    text-indent .2rem
  .item
    overflow hidden
    display flex
    height 1.9rem
    .item-img
      width 1.7rem
      height 1.7rem
      padding .1rem
    .item-info
      flex 1
      padding .1rem
      min-width 0
      .item-title
        line-height .54rem
        font-size .32rem
        ellipse()
      .item-desc
        line-height: .4rem;
        color #ccc
        ellipse()
      .item-btn
        line-height .44rem
        margin-top .16rem
        background #ff9300
        padding 0 0.2rem
        border-radius .06rem
        color #fff
</style>
