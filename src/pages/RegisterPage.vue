<template>
  <b-form class="formulario">
    <label class="sr-only" for="inline-form-input-name">Usuario</label>
    <b-form-input
      v-model="usuario"
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="Usuario"
    ></b-form-input>

    <label class="sr-only" for="inline-form-input-username">Password</label>
    <b-input-group class="mb-2 mr-sm-2 mb-sm-0">
      <b-form-input
        v-model="password"
        id="inline-form-input-username"
        placeholder="password"
      ></b-form-input>
    </b-input-group>
    <label class="sr-only" for="inline-form-input-username">email</label>
    <b-input-group class="mb-2 mr-sm-2 mb-sm-0">
      <b-form-input
        v-model="email"
        id="inline-form-input-username"
        placeholder="mail"
      ></b-form-input>
    </b-input-group>

    <b-button @click="createUser" variant="primary">Register</b-button>
  </b-form>
</template>
<script>
import axios from "axios";
export default {
  name: " RegisterPage",
  data() {
    return {
      usuario: "",
      password: "",
      email: "",
    };
  },
  methods: {
    async createUser() {
      const newUser = {
        usuario: this.usuario,
        password: this.password,
        email: this.email,
        isAdmin: false,
      };
      let resp = await axios.post(
        "https://62e1c00cfa99731d75dbab30.mockapi.io/usuarios",
        newUser
      );
      this.usuarios = resp.data;
      this.$router.push('/login')
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.formulario {
  text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    width: 300px;
    height: 150px;
    margin-left: 550px;
    margin-top: 150px;
  
}
</style>