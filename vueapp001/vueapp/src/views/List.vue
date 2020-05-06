<template>
  <div>
     <ul>
      <li class="icons" v-for="(item,index) in pageLists"
          :key="index">
       {{item.title}}-{{item.content}}
      </li>
       </ul>
  </div>
</template>
<script>
import Store from '@/store';

export default {
  name: 'List',
  Store,
  mounted() {
    window.Vue = this;
  },
  computed: {
    pageLists() {
      return Store.state.lists;
    },
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

<style scoped lang="scss">
  li{
    list-style: none;
  }
 .footer{
   position: fixed;
   width: 100%;
   height: 60px;
   line-height: 60px;
   left: 0;
   bottom: 0;
   display: flex;
   flex-flow: row nowrap;
   justify-content: space-around;
  }
  .icons{
    font-size: 16px;
    flex: 1;
    text-align: center;
    border-top: 1px solid #0055ff;
  }
  a{
    color: #32a1ce;
    display: block;
    &.active{
      color: #fff;
      background: #0055ff;
    }
  }
</style>
