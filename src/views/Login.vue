<template>
  <div class="container mt-5">
    <the-login/>
  </div>
</template>

<script>
// import TheLogin from '@/components/auth/TheLogin.vue';
import TheLogin from '../components/auth/TheLogin.vue'

export default {
    name: 'Login',
    components: {
        TheLogin,
  },
};
</script>
