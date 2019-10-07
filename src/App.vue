<template>
  <div id="app">
    <Header></Header>
    <Sidebar v-show="$route.path === '/Dashboard' || $route.path === '/Subjects'|| $route.path === '/EditProfile' || $route.path === '/PersonalInfo' || $route.path ==='/update'? true: false "> 
  </Sidebar>
  
  <AppBody></AppBody>
  </div>
</template>

<script>
import Sidebar from 'router/frame/Sidebar.vue'
import Header from 'router/frame/Header.vue'
import AppBody from 'router/frame/Body.vue'

export default {
  name: 'app',
  components: {
    Header,
    AppBody,
    Sidebar
  }
}
</script>
