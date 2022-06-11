<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">北京</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hotCities" :key="item.id">
            <div class="button">{{ item.name }}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{ key }}</div>
        <div class="item-list">
          <div
            class="item border-topbottom"
            v-for="innerItem of item"
            :key="innerItem.id"
          >
            {{ innerItem.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import BetterScroll from 'better-scroll'
export default {
  name: 'CityList',
  components: {
  },
  props: {
    hotCities: Array,
    cities: Object
  },
  watch: {
    letter () {
      if (this.letter) {
        console.log(this.letter)
        console.log(this.bScroll)
        this.bScroll.scrollToElement(this.$refs[this.letter][0])
      }
    }
  },
  data () {
    return {
      bScroll: undefined,
      letter: ''
    }
  },
  mounted () {
    setTimeout(() => {
      this.bScroll = new BetterScroll(this.$refs.wrapper)
    }, 80)
    this.$bus.$on('change-letter', (data) => {
      console.log('change-letter')
      this.letter = data
    })
  },
  beforeDestroy () {
    this.$bus.$off('change-letter')
  }
}
</script>
<style lang="stylus" scoped>
@import "~%styles/varibles.styl"
.border-topbottom
  &:before
    border-color #ccc
  &:after
    border-color #ccc
.border-bottom
  &:before
    border-color #ccc
.list
  overflow hidden
  position absolute
  top 1.78rem
  bottom 0rem
  left 0
  right 0
.title
  height .54rem
  line-height .54rem
  background #eee
  padding-left .2rem
  color #666
  font-size .26rem
.button-list
  overflow hidden
  padding .1rem .6rem .1rem .1rem
.button-wrapper
  float left
  width 33.33%
  .button
    margin .1rem
    padding .1rem 0
    text-align center
    border .02rem solid #ccc
    border-radius .06rem
.item-list
  .item
    line-height .76rem
    padding-left .2rem
</style>
