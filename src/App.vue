<template>
  <div id="app">
    <Navbar />
    <router-view></router-view>
  </div>
</template>

<script>
//Navbar가져오기
import Navbar from './components/Navbar.vue'

export default {
  name: 'app',
  components: {Navbar},
  data () {
    return {
      
    }
  }
}
</script>

<style>

</style>
