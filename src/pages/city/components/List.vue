<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{ $store.state.city }}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper"
               v-for="item of hotCities"
               :key="item.id"
               @click="handleCityClick(item.name)"
          >
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
            @click="handleCityClick(innerItem.name)"
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
        this.bScroll.scrollToElement(this.$refs[this.letter][0])
      }
    },
    cities () {
      this.$nextTick(() => {
        this.bScroll.refresh()
      })
    }
  },
  data () {
    return {
      bScroll: undefined,
      letter: ''
    }
  },
  mounted () {
    this.bScroll = new BetterScroll(this.$refs.wrapper, {click: true})
    this.$bus.$on('change-letter', (data) => {
      this.letter = data
    })
  },
  beforeDestroy () {
    this.$bus.$off('change-letter')
  },
  methods: {
    handleCityClick (city) {
      this.$store.commit('changeCity', city)
      this.$router.back()
    }
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
    height 0.3rem
    line-height 0.3rem
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
