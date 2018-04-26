<template>
  <div id="app">
    <img src="./assets/logo.png"> <br />
    Date
    <VueDatetimePicker v-model='date' type='date' format='DD/MM/YYYY'></VueDatetimePicker>
    Time
    <VueDatetimePicker v-model='time' type='time' format='HH:mm'></VueDatetimePicker>
    Datetime
    <VueDatetimePicker v-model='datetime' type='datetime' format='DD/MM/YYYY HH:mm'></VueDatetimePicker>
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
      date: '2018-12-28',
      time: '2018-12-28T13:09:00.000Z',
      datetime: '2018-12-28T13:09:00.000Z'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
