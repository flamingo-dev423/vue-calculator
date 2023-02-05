<template>
  <div class="bg-gray-700 h-screen w-full pt-32">

    <vueCalculator />
  </div>


 <router-view />
</template>

<script>
import vueCalculator from './components/vue-calculator.vue'

export default {
  name: 'App',
  components: {
    vueCalculator
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@200;300;400;500;600&display=swap');
* {
    /* border: 1px solid red; */
}

</style>
