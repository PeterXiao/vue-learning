<template>
  <div>
    hello info component
     <button type="button"  v-on:click="add()">添加</button>
  </div>
</template>
<script>
import Store from '@/store';

export default {
  name: 'Info',
  Store,
  mounted() {
    window.Vue = this;
  },
  methods: {
    add() {
      // debugger;
      console.log('add event');
      Store.commit('increase');
    },

  },
};
</script>

<style scoped>
</style>
