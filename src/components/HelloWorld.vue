<template>
  <div class="hello">
    <sly-container />
  </div>
</template>

<script>
import SlyContainer from './SlyContainer.vue'

export default {
  name: 'HelloWorld',
  components: {
    'sly-container': SlyContainer
  },
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
