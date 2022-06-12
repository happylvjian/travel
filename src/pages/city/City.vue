<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" :hotCities="hotCities"></city-list>
    <city-alphabet :cities="cities"></city-alphabet>
  </div>
</template>
<script>
import axios from 'axios'
import CityHeader from '../city/components/Header'
import CitySearch from '../city/components/Search'
import CityList from '../city/components/List'
import CityAlphabet from '../city/components/Alphabet'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      cities: {},
      hotCities: []
    }
  },
  mounted () {
    this.getCityInfo()
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json').then(res => {
        res = res.data
        if (res.ret && res.data) {
          const data = res.data
          this.cities = data.cities
          this.hotCities = data.hotCities
        }
      })
    }
  }
}
</script>
<style lang="stylus" scoped>

</style>
