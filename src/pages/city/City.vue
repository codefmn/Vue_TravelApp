<template>
  <div>
    <city-header></city-header>
    <city-search></city-search>
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
    axios.get('/api/city.json')
      .then(response => response.data)
      .then(response => {
        if (response.ret && response.data) {
          this.hotCities = response.data.hotCities
          this.cities = response.data.cities
        }
        console.log(response)
      })
  }
}
</script>
