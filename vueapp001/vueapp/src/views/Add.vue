<template>
  <div>
    <p>标题</p>
    <input type="text" v-model="title"  class="icons">
    <p>内容</p>
    <input type="text" v-model="content" class="icons">
     <button type="button"  v-on:click="add()" >添加</button>
  </div>
</template>
<script>
import Store from '@/store';

export default {
  name: 'Add',
  Store,
  data() {
    return {
      title: '',
      content: '',
    };
  },
  mounted() {
    window.Vue = this;
  },
  methods: {
    add() {
      // debugger;
      console.log('add event');
      Store.commit('addItem', {
        title: this.title,
        content: this.content,
      });
      this.title = '';
      this.content = '';
      this.$router.push('/home/list');
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
