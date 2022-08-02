<template>
  <div>
    <div v-for="(item, index) in products" :key="index">
      <div class="productos">
        <div class="card" style="width: 18rem">
          <h5 class="card-title text-center">{{ item.titulo }}</h5>
          <img class="img-card" :src="item.imagen" alt="" />
           <td> <p class='btn btn-warning' @click="editarProducto(item.id)" >Editar</p></td>
          <div class="card-body">
            <p class="card-text">${{ item.precio }}</p>
            <button class="btn btn-success text-center">Agregar</button>
          </div>
        </div>
      </div>
    </div>
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
      this.$router.push({ name: "editar", params: { id: payload } });
    },
  },
  async mounted() {
    // let isLogged = localStorage.getItem("isLogged");
    // let isAdmin = localStorage.getItem("isAdmin");
    // if (isLogged != "true") {
    //   this.$router.push("/login");
    // }
    // if (isAdmin != "true") {
    //   this.$router.push("/main");
    // }
    let resp = await axios.get(
      "https://62e1c00cfa99731d75dbab30.mockapi.io/api/products"
    );

    this.products = resp.data;
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.productos {
  text-align: center;
  padding: 15px;
  margin: auto;
  margin-top: 40px;
  margin-right: 30px;
  border-radius: 10px;
  box-shadow: 1px 4px 10px 0 brown;
  float: right;
}
.img-card {
  width: 150px;
  height: 150px;
}
.product {
  margin: 75px;
}
</style>
