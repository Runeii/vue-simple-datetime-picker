<template>
  <div id="app">
    <img src="./assets/logo.png">
    <VueDatetimePicker v-model='blank' format='YYYY-MM-DD HH:mm'></VueDatetimePicker>
  </div>
</template>

<script>
import VueDatetimePicker from './components/VueDatetimePicker'

export default {
  name: 'app',
  components: {
    VueDatetimePicker
  },
  data () {
    return {
      blank: '2012-07-09 19:22:09.1440844Z'
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
}
</style>
