<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list
      :hotCities="hotCities"
      :cities="cities"
      :letter="letter"
    ></city-list>
    <city-alphabet
      :cities="cities"
      @change="handleLetterChange"
    ></city-alphabet>
  </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
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
      hotCities: [],
      cities: {},
      letter: ''
    }
  },
  methods: {
    handleLetterChange (letter) {
      this.letter = letter
    }
  },
  mounted () {
    axios.get('https://www.easy-mock.com/mock/5b8ec1bb9125da0e4952ad30/travel/city')
      .then(response => response.data)
      .then(response => {
        if (response.ret && response.data) {
          this.hotCities = response.data.hotCities
          this.cities = response.data.cities
        }
      })
  }
}
</script>
