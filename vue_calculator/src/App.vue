<template>
  <div class="navContainer">
    <Head_app navOne="Calculator classic" navTwo="About">
    </Head_app>
  </div>

  <div class="mainContainer">
    <router-view DevA="Carlos Eduardo Cabrera Miranda" DevB="Alvaro Felipe Avila Vidal" DevC="Juan Jose Urbano Perdomo"
      DevD="Yhonathan Camilo Gomez Camacho" DevE="Nicolas Alejandro Ruiz" />
  </div>
</template>

<script>



import Head_app from './components/Head.vue';


export default {
  name: 'App',
  components: {
    Head_app,
  }
}
</script>

<style>



#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
}
</style>
