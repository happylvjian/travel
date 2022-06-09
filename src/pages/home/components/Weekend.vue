<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="item in recommendedList " :key="item.id">
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
  name: 'HomeWeekend',
  data () {
    return {
      recommendedList: [
        {
          id: '0001',
          imgUrl: 'https://img1.qunarzz.com/travel/poi/1504/60/1d8518f48e5283.jpg_r_640x290x70_29c73fbf.jpg',
          title: '大连圣亚海洋世界',
          desc: '浪漫大连首站，狼浪漫的海洋主题乐园'
        },
        {
          id: '0002',
          imgUrl: 'https://img1.qunarzz.com/travel/poi/1504/60/1d8518f48e5283.jpg_r_640x290x70_29c73fbf.jpg',
          title: '大连圣亚海洋世界',
          desc: '浪漫大连首站，狼浪漫的海洋主题乐园'
        },
        {
          id: '0003',
          imgUrl: 'https://img1.qunarzz.com/travel/poi/1504/60/1d8518f48e5283.jpg_r_640x290x70_29c73fbf.jpg',
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
  font-size .32remS
  background #eee
  text-indent .2rem
.item-img-wrapper
  overflow hidden
  height 0
  padding-bottom 53.4%
  .item-img
    width 100%
.item-info
  padding .1rem
  .item-title
    line-height .54rem
    font-size .32rem
    ellipse()
  .item-desc
    line-height: .4rem;
    color #ccc
    ellipse()
</style>
