<template>
  <div>
    <div
      class="item"
      v-for="(item, index) in list"
      :key="index"
    >
      <div class="item-title border-bottom">
        <div class="item-title-icon"></div>
        <div>{{item.title}}</div>
      </div>
      <detail-list
        v-if="item.children"
        class="item-children"
        :list="item.children"
      >
      </detail-list>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DetailList',
  components: {
  },
  props: {
    list: Array
  }
}
</script>
<style lang="stylus" scoped>
.item-title
  height .8rem
  line-height .8rem
  font-size .32rem
  display flex
  align-items center
  padding 0 .2rem
  .item-title-icon
    width .36rem
    height .36rem
    background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
    margin-right .1rem
    background-size .4rem 3rem
.item-children
  padding-left .2rem
</style>
