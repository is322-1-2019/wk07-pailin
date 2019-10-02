<template>
    <div class="container" id="maincard">
      <div class="card" id="maincard">
        <data-in></data-in>
        <parent-of-patient></parent-of-patient>
        <allergic></allergic>
        <yomrub></yomrub>
        <application></application>
      </div>
    </div>
</template>

<script>
import dataIn from './incard/dataIn.vue'
import parentOfPatient from './incard/parentOfPatient.vue'
import allergic from './incard/allergic.vue'
import yomrub from './incard/yomrub.vue'
import application from './incard/application.vue'

export default {
  components: {
    dataIn,
    parentOfPatient,
    allergic,
    yomrub,
    application
  }
}
</script>

<style>
#maincard {
  background-color: antiquewhite
}
</style>