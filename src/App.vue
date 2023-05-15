<template>
<div class="header">
    <h1>Milkdrop Generator</h1>
    <p>Milkdrop generator est un projet qui permet de créer vos visualisations winamp et projectM à la volée.</p>
    <img src="./assets/visual.png"/>
</div>
  <MilkGenerator/>
</template>

<script>

import MilkGenerator from './components/Generator.vue'

export default {
  name: 'App',
  components: {
    MilkGenerator
  }
}
</script>

<style>
        html,body{           font-family:Arial;margin:0;padding:0;}
#app {
   font-family:Arial;margin:0;padding:0;
}
        .header{background:red;padding:10px 0 50px 0;color:#fff;text-align:center;}
</style>
