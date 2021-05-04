<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <PeopleTable />
  </div>
</template>

<script>
import PeopleTable from './components/PeopleTable.vue'

export default {
  name: 'App',
  components: {
    PeopleTable
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
