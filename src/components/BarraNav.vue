ines (17 sloc) 380 Bytes

<template>
  <div>
    <b-nav tabs fill>
      <b-nav-item>
        <router-link to="/login">Login</router-link>
      </b-nav-item>
      <b-nav-item
        ><router-link to="/register">Register</router-link></b-nav-item
      >
      <b-nav-item><router-link to="/main">main</router-link> </b-nav-item>
      <b-nav-item> </b-nav-item>

      <button class="btn btn-outline-dark">Carrito</button>
    </b-nav>
  </div>
</template>

<script>
export default {
  name: "BarraNav",
};
</script>

<style scoped></style>
