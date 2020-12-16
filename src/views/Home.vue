<template>
  
  <div id="app" style="width: 1000px">
    <div class="home">
      <the-home/>
    </div>
  </div>

</template>

<script>
import HelloWorld from '../components/HelloWorld.vue'
// @ is an alias to /src
// import TheHome from '@/components/TheHome.vue'
import TheHome from '../components/TheHome.vue'

export default {
  name: 'Home',
  components: {
    TheHome,
    HelloWorld
  }
}
</script>
