<template>
  <div>
    <h1>ERES ADMIN</h1>

    <table>
      <tr
        v-for="(item, index) in products"
        :key="index"
      >
        <td>{{ item.titulo }}</td>
        <td>{{ item.precio }}</td>
        <td>{{ item.detail }}</td>
        <td @click="editarProducto(item.id)">Editar</td>
      </tr>
    </table>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "AdminPage",
  data() {
    return {
      products: [],
      selected: 0,
    };
  },
  methods: {
    editarProducto(payload) {
      /*eslint-disable*/
      debugger
      this.$router.push({ name: "editar", params: { id: payload } });
    },
  },
  async mounted() {
    
    let isLogged = localStorage.getItem("isLogged");
    let isAdmin = localStorage.getItem("isAdmin");
    if (isLogged != "true") {
      this.$router.push("/login");
    }
    if (isAdmin != "true") {
      this.$router.push("/main");
    }
    let resp = await axios.get(
      "https://62e1c00cfa99731d75dbab30.mockapi.io/api/products"
    );
    this.products = resp.data;
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
