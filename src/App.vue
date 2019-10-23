<template>
  <div id="app">
    <Main></Main>
    <test-province></test-province>
  </div>
</template>

<script>
import Main from './components/incard/Main.vue'
import testProvince from './components/incard/testProvince.vue'

export default {
  name: 'app',
  components: {
    Main,
    testProvince
  }
}
</script>
