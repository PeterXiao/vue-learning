<template>
  <div>
    hello info component
    <div>
      <ul>
       <li v-for="(item,index) in Lists"
           @click="choose(index)"
           :class="{active: index == current && current != ''}"
           :key="index">
        {{item}}
       </li>
        </ul>
        <button type="button" @click="mdd()">添加</button>
        <ul>
          <li v-for="(item,index) in target" :key="index">{{item}}</li>
        </ul>
    </div>

     <button type="button"  v-on:click="add()">转移</button>
  </div>
</template>
<script>
import Store from '@/store';

export default {
  name: 'Demo',
  Store,
  data() {
    return {
      current: '',
      Lists: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      target: [],
    };
  },
  mounted() {
    window.Vue = this;
  },
  methods: {
    add() {
      // debugger;
      console.log('add event');
      Store.commit('increase');
    },
    mdd() {
      // debugger;
      if (this.current === '') return;
      console.log('add event');
      this.$data.target.push(this.$data.Lists[this.current]);
      this.current = '';
    },
    choose(index) {
      console.log(index);
      this.$data.current = index;
    },

  },
};
</script>

<style scoped>
  li.active{
    background-color: green;
  }
</style>
