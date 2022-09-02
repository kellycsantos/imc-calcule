<template>
  <div id="app">
    <PageView>
      <ImcCalc />
    </PageView>
  </div>
</template>

<script>
import ImcCalc from './components/ImcCalc.vue'
import PageView from './views/ViewCalc.vue'

export default {
  name: 'App',
  components: {
    ImcCalc,
    PageView
  }
}
</script>

<style scoped >
#app {
  /* box-sizing: border-box; */
  font-family: Roboto, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #FFF;
  background: #0C0E1B ;
  margin: 0px;
  height: 100vh;
  padding: 0 2px;
}
</style>
