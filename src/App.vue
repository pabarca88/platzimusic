<template>
  <div id="app">
    <h1>Top Artist</h1>
    <select v-model="selectedCountry" class="" name="">
      <option v-for="country in countries" :value="country.value">{{ country.name }}</option>
    </select>
    <!-- <input type="text" name="" v-model="pais"> -->
    <button type="button" @click="refreshArtists">Buscar</button>
    <spinner v-show="loading"></spinner>
    <ol>
      <artist v-for="artist in artists" :artist="artist" :key="artist.mbid"></artist>
    </ol>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Artist from './components/Artist.vue'
import Spinner from './components/Spinner.vue'
import getArtists from './api'

export default {
  name: 'app',
  data () {
    return {
      artists: [],
      countries: [
        { name: 'Argentina', value: 'argentina' },
        { name: 'Colombia', value: 'colombia' },
        { name: 'España', value: 'spain' },
        { name: 'Chile', value: 'chile' }
      ],
      selectedCountry: 'argentina',
      loading: true
    }
  },
  filters: {
    uppercase: function (str) {
      return str.toUpperCase()
    }
  },
  components: {
    Artist,
    Spinner
  },
  methods: {
    refreshArtists() {
      const self = this
      this.loading = true
      this.artists = []
      getArtists(this.selectedCountry)
        .then(function (artists) {
          self.loading = false
          self.artists = artists
        })
    }
  },
  mounted: function () {
    this.refreshArtists()
  },
  watch: {
    selectedCountry() {
      this.refreshArtists()
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 600px;
  margin: 0 auto;
}
ul {
  list-style: none;
}
ol{
  text-align: left;
}
ul li{
  display: inline-block;
  margin: 0 10px;
}
</style>
