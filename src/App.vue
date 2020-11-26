<template>
  <div id="app">
    <KonvaStage />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import KonvaStage from '@/components/KonvaStage.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    KonvaStage
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
