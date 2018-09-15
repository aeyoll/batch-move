<template>
  <div id="app">
    <Grid :items="items" />
  </div>
</template>

<script>
import Grid from './components/Grid'

export default {
  name: 'App',
  components: {
    Grid
  },
  data: function () {
    return {
      items: [
        {
          name: 'Lorem ipsum',
          image: 'https://placekitten.com/160/50',
          selected: false,
          position: 1
        }, {
          name: 'dolor sit',
          image: 'https://placekitten.com/160/50',
          selected: false,
          position: 2
        }, {
          name: 'consectetur',
          image: 'https://placekitten.com/160/50',
          selected: false,
          position: 3
        }, {
          name: 'Molestias',
          image: 'https://placekitten.com/160/50',
          selected: false,
          position: 4
        }, {
          name: 'illum possimus',
          image: 'https://placekitten.com/160/50',
          selected: false,
          position: 5
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px auto;
  width: 1400px;
}
</style>
