<template>
  <div id="app">
    <Nav />
    <router-view />
  </div>
</template>

<script>
import Nav from '@/components/layout/Nav';

export default {
  name: 'App',
  components: {
    Nav
  }
}
</script>

<style lang='sass'>
*
  margin: 0
  box-sizing: border-box
  text-decoration: none
  color: white

#app
  background: #202020
  min-height: 100vh
  padding: 50px 9vw


</style>
