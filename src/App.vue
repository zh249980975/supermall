<template>
  <div id="app">
    <router-view></router-view>
    <main-tab-bar/>
  </div>
</template>

<script>
import MainTabBar from 'components/content/mainTabbar/MainTabBar'

  export default{
    name:'app',
    components:{
      MainTabBar
    }
  }
</script>

<style>

</style>
