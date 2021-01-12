<template>
  <div>
   
    <CheckAll/>,
    <SoloCheck/>

  </div>
</template>

<script>

import CheckAll from './components/CheckAll.vue'
import SoloCheck from './components/SoloCheck.vue'

export default {
  name: 'App',
  components: {
    CheckAll,SoloCheck
  }
}
</script>

<style>

</style>
