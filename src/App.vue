<template>
  <div class="fondo">
    <MenuNavbar />
    <AppConvertidor />
  </div>

  

 </template>

<script>
import MenuNavbar from './components/MenuNavbar';
import AppConvertidor from './components/AppConvertidor';


export default {
  name: 'App',
  components: {
    MenuNavbar,
    AppConvertidor
   
  }
}
</script>

<style>
.fondo{
  background-image: url('./assets/fondovue.jpg');
  height: 100vh;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}
</style>
