<template>
  <div>
    <div class="form">
      <b-form class="formulario">
        <label class="sr-only" for="inline-form-input-name">usuario</label>
        <b-form-input
          id="inline-form-input-name"
          class="mb-2 mr-sm-2 mb-sm-0"
          placeholder="Usuario"
          v-model="usuario"
        ></b-form-input>

        <label class="sr-only" for="inline-form-input-username">password</label>
        <b-input-group class="mb-2 mr-sm-2 mb-sm-0">
          <b-form-input
            id="inline-form-input-username"
            placeholder="password"
            v-model="password"
          ></b-form-input>
        </b-input-group>

        <b-button @click="validarLogin" variant="primary">Login</b-button>
      </b-form>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "LoginPage",
  data() {
    return {
      usuario: "",
      password: "",
      usuarios: [],
    };
  },
  methods: {
    validarLogin() {
    
      let data = this.usuarios.find(
        (o) => o.usuario === this.usuario && o.password === this.password
      );
      localStorage.clear();
      if (data) {
        localStorage.setItem("isLogged", "true");
        if (data?.isAdmin) {
          localStorage.setItem("isAdmin", "true");
          this.$router.push("admin");
        } else {
          localStorage.setItem("isAdmin", "false");
          this.$router.push("main");
        }
      }
    },
  },
  async mounted() {
    let resp = await axios.get(
      "https://62e1c00cfa99731d75dbab30.mockapi.io/api/usuarios"
    );
    console.log(resp);
    this.usuarios = resp.data;
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