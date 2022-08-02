<template>
    <div class="container">
        <h1>Administrador</h1>
        <form action="">
            <div class="row">
                <div class="col-3">
                    <label for="name">Name:</label>
                </div>
                <div class="col-9">
                    <input class="form-control" type="text" id="name" placeholder="Name Product" v-model="titulo"/>
                </div>
            </div>

            <div class="row">
                <div class="col-3">
                    <label for="price">$:</label>
                </div>
                <div class="col-9">
                    <input class="form-control" type="number" id="price" v-model="precio">
                </div>
            </div>
            <div class="row">
                <div class="col-3">
                    <label for="stock">Stock:</label>
                </div>
                <div class="col-9">
                    <input class="form-control" type="number" id="stock" v-model="cantidad">
                </div>
            </div>
            <div>
                <input type="button" class="btn btn-primary" @click="ActualizarProducto()" value="Editar Producto"/>
                <router-link to="/admin" class="btn btn-warning">Atras</router-link>
            </div>
        </form>
    </div>
</template>
<script>
import axios from "axios";
export default {
  name: "EditarPage",
  data() {
    return {
     
        titulo: '',
        detail:'',
        cantidad:'',
        precio: 0,
      
    };
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
    let paramId = this.$route.params.id
    let resp = await axios.get(
      "https://62e6d7cd69bd03090f764b0b.mockapi.io/api/productos/" + paramId
    );
    this.product = resp.data;
  },
  methods: {
    async ActualizarProducto() {
      let resp = await axios.put(
        "https://62e6d7cd69bd03090f764b0b.mockapi.io/api/productos/" + this.$route.params.id,
        this.product
      );
       console.log(resp);
      alert('Producto actualizado')
    },
  }
};
</script>
<style scoped>

.container{
    text-align: center;
    width: 500px;
    margin-top: 150PX;
}

</style>