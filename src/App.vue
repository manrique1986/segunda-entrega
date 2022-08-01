<template>
  <div id="app">
    <barra-nav/>
    <router-link to="/login">Login</router-link>
    <router-link to="/register">Register</router-link>
    <router-link to="/main">Main</router-link>
    <router-link to="/admin">Admin</router-link>
    <a @click="desloguear">Desloguear</a>
    <router-view></router-view>
  </div>
</template>

<script>
import BarraNav from './components/BarraNav.vue';
export default {
  name: "App",
  components: {BarraNav },
  data() {
    return {
    };
  },
  methods: {
    desloguear(){
      localStorage.clear()
      this.$router.push('login')
    }
  }
};
</script>

<style>


</style>
