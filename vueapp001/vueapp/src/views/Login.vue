<template>
  <div>
  <form action="" v-if="!isReg">
    用户名
    <input type="text" v-model="name">
    密码
    <input type="password" v-model="password">
    <button type="button" @click="login()">登录</button>
    <button type="button" @click="reg()">注册</button>
  </form>
  <form v-else>
    <div>
      用户名
      <input type="text" v-model="name">
      密码
      <input type="password" v-model="password">
      再次让用户输入密码
      <input type="password" v-model="repeat">
       <button type="button" @click="addUser()">确定</button>
       <button type="button"  v-on:click="cancel()">取消</button>
    </div>
  </form>
  </div>
</template>
<script>
import Store from '@/store';

export default {
  name: 'Login',
  Store,
  data() {
    return {
      isReg: false,
      name: '',
      password: '',
      repeat: '',
    };
  },
  methods: {
    add() {
      // debugger;
      console.log('add event');
      Store.commit('increase');
    },
    reg() {
      // debugger;
      // console.log('add event');
      this.isReg = true;
    },
    login() {
      // debugger;
      // console.log('add event');
      if (localStorage.getItem('name') === this.name && localStorage.getItem('password') === this.password) {
        this.$router.push('/home/list');
      } else {
        alert('密码or 名称不正确！，请重新输入！');
      }
    },
    addUser() {
      // debugger;
      // console.log('add event');
      if (this.password === this.repeat) {
        localStorage.setItem('name', this.name);
        localStorage.setItem('password', this.password);
        this.name = '';
        this.password = '';
        this.isReg = false;
      } else {
        alert('两次密码输入不一致！，请重新输入！');
      }
    },
    cancel() {
      // debugger;
      // console.log('add event');
      this.isReg = false;
      localStorage.setItem('password', this.password);
    },
  },
};
</script>

<style scoped>
</style>
