<template>
  <div id="app">
    <barra-nav/>
    <b-button class="button" @click="desloguear" variant="warning">Desloguear</b-button>
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

<style scoped>

.button{


  margin: 0%;
  position: absolute;

}


</style>
