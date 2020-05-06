<template>
  <div>
    <router-view/>
    <ul class="footer">
      <li class="icons"><router-link :to="{name: 'list'}">新闻列表</router-link></li>
      <li class="icons"><router-link :to="{name: 'add'}">个人中心</router-link></li>
      <!-- <li class="icons"><router-link :to="{name: 'user'}">维护列表</router-link></li> -->
    </ul>

    <!-- <img alt="Vue logo" src="../assets/logo.png" > -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
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
