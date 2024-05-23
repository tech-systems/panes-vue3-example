<template>
  <div class="panes-component">
      <h1>Panes Demo</h1>
      <p hide-on-bottom>Content</p> 
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import { CupertinoPane, CupertinoSettings } from 'cupertino-pane';


export default {
  name: 'PanesComponent',
  emits: ['panes:init'],
  props: {
    settings: {
      type: CupertinoSettings,
      required: false
    }
  },

  setup(props, { emit }) {
    const pane = ref();

    onMounted(() => {
      console.log('settigs', props.settings);
      if (pane.value) {
        return;
      }
      pane.value = new CupertinoPane('.panes-component', props.settings);
      emit('panes:init', pane.value);
    });
  }
}

</script>