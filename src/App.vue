<template>
  <div id="app">
    <Main></Main>
    <p>----------------------------------------</p>
    <test-province></test-province>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import testProvince from './components/incard/testProvince.vue'

export default {
  name: 'app',
  components: {
    Main,
    testProvince
  }
}
</script>
