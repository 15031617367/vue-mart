<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>|
      <router-link to="/login" v-if="!isLogin">Login</router-link>
      <a @click="logout" v-if="isLogin">logout</a>
    </div>
    <router-view/>
  </div>
</template>
<script>
  import {mapGetters} from "vuex"
  export default {
    methods:{
      logout(){
        this.$http({
          methods:'get',
          url:"/api/logout"
        }).then((response)=>{
          console.log("退出测试")
          console.log(response)
        })
      }
    },
    computed:{
      ...mapGetters(['isLogin'])
    }
  }
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
