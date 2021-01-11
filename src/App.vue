<template>
  <div ID="app">
    <User/>
  </div>
</template>



<script>

import User from './components/UserProfile.vue';

export default {
  name: 'App',
  components:{
    User
  },
 
 

  
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000e1b;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>
