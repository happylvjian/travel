<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
  name: 'Home',
  components: {
    HomeWeekend,
    HomeRecommend,
    HomeHeader,
    HomeSwiper,
    HomeIcons
  },
  computed: {
    ...mapState(['city'])
  },
  data () {
    return {
      // 用于保存改变城市之前的city值
      lastCity: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.getHomeInfo()
      this.lastCity = this.city
    }
  },
  methods: {
    getHomeInfo () {
      axios.get(`/api/index.json?city=${this.city}`).then(res => {
        res = res.data
        if (res.ret && res.data) {
          let data = res.data
          this.swiperList = data.swiperList
          this.iconList = data.iconList
          this.recommendList = data.recommendList
          this.weekendList = data.weekendList
        }
      })
    }
  }
}
</script>
<style lang="stylus" scoped>
</style>
