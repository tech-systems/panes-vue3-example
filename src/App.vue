<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>Panes Demo</h1>

  <PanesComponent :settings="settings" @panes:init="handleValueEmitted"/>
</template>

<script>
import { ref } from 'vue';
import PanesComponent from './components/PanesComponent.vue'

export default {
  name: 'App',
  components: {
    PanesComponent
  },
  data() {
    return {
      settings: {
        fitHeight: false
      }
    };
  },
  setup() {
    const panes = ref('');

    const handleValueEmitted = async(value) => {
      panes.value = value;

      // Present pane using control over it from parent component
      await panes.value.present({animate: true});
    };

    return {
      panes,
      handleValueEmitted
    };
  }
}
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
