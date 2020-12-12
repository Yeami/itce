<template>
  <div id="app">
    <WrapperComponent/>
  </div>
</template>

<script>
import WrapperComponent from './components/WrapperComponent.vue'

export default {
  name: 'App',
  components: {
    WrapperComponent
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  .ant-tabs .ant-tabs-top-content > .ant-tabs-tabpane, .ant-tabs .ant-tabs-bottom-content > .ant-tabs-tabpane {
    display: flex;
    justify-content: center;
  }
}
</style>
