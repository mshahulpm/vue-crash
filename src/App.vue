<template>
<div class="container">
  <router-view></router-view>
<Footer/>
</div>
</template>

<script>

import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Footer
  },
 
}
</script>

<style>
*{
  box-sizing: border-box;
  font-family: 'Poppins',sans-serif ;
}
.container{
  width: 90%;
  max-width: 500px;
  border-radius: 4px;
  box-shadow: 1px 1px 2px 2px rgb(197, 186, 186);
  min-height: 200px;
  margin: auto;
  margin-top: 50px;
  padding-left: 20px;
  padding-bottom: 30px;
  margin-bottom: 30px;
}
</style>
