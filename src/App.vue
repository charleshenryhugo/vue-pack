<template>
  <div id="app">
    <RecentActivityBar/>
    <IspRadar/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld'
import IspRadar from '@/components/IspRadar'
import RecentActivityBar from '@/components/RecentActivityBar'

export default {
  name: 'App',
  components: {
    HelloWorld,
    IspRadar,
    RecentActivityBar
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
