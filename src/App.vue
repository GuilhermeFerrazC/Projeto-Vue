<template>
  <div id="app">
    <JogoComponent />
  </div>
</template>

<script>
import JogoComponent from './components/JogoComponent.vue';

export default {
  name: 'App',
  components: {
    JogoComponent
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
