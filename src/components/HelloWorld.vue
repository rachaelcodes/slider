<template>
  <div class="hello">
    <sly-container :views="views">
      <sly-view v-for="view in views" :key="view" :slot="view" :num="view"/>
    </sly-container>
  </div>
</template>

<script>
import SlyContainer from './SlyContainer.vue'
import SlyView from './SlyView.vue'

export default {
  name: 'HelloWorld',
  components: {
    'sly-container': SlyContainer,
    'sly-view': SlyView,
  },
  data() {
    return {
      views: ['one', 'two', 'three']
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
