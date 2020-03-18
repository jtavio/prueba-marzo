<template>
  <div id="app">
    <Barnav />
    <div class="container">
      <div class="row justify-content-around my-4">
        <div col="5">
          <SelecConcess />
        </div>
        <div col="5">
          <a type="button" class href="#" @click="cart = true">
            <i class="fas fa-plus-circle fa-3x" style="color:DodgerBlue"></i>
          </a>
        </div>
      </div>
       <table class="table table-hover table-bordered shadow p-3 mb-5 bg-white rounded">
        <thead class="thead-dark">
          <tr>
            <th scope="col">#</th>
            <th scope="col">Nombre</th>
            <th scope="col">Apellido</th>
            <th scope="col">Direccion</th>
            <th scope="col">Status</th>
            <th scope="col">Asignado</th>
            <th scope="col">Opciones</th>
          </tr>
        </thead>
        <tbody v-for="prod in productos" :key="prod.id">
         <tabla :producto="prod" v-on:borrar-item="BorrarEstado"></tabla>
        </tbody>
      </table>
      
      <!-- Content here -->
    </div>
    <!-- add modal -->
    <form action>
      <mdb-modal size="lg" :show="cart" @close="cart = false" class="text-center">
        <mdb-modal-header>
          <h4 class="modal-title" id="myModalLabel">Add client</h4>
        </mdb-modal-header>
        <mdb-modal-body>
          <section class="preview">
            <div class="row">
              <div class="col">
                <input type="text" class="form-control" placeholder="First name" v-model="TextName" />
              </div>
              <div class="col">
                <input
                  type="text"
                  class="form-control"
                  placeholder="Last name"
                  name="LastName"
                  v-model="LastName"
                />
              </div>
            </div>

            <mdb-input label="Dirección de habitanción" v-model="direccion" />
            <select class="browser-default custom-select" v-model="concess">
              <option disabled value>Select concessionaire</option>
              <option>One</option>
              <option>Two</option>
              <option>Three</option>
            </select>
          </section>
        </mdb-modal-body>
        <mdb-modal-footer>
          <mdb-btn outline="primary" @click="cart = false">Close</mdb-btn>
          <mdb-btn color="primary" @click="guardar" v-on:click="cart = false">Add</mdb-btn>
        </mdb-modal-footer>
      </mdb-modal>
    </form>
  </div>
</template>
<script>
import productos from "@/productos.json";
import Barnav from "@/components/Barnav";
import SelecConcess from "@/components/SelectConcessionari";
import Tabla from "@/components/Tabla";
import {
  mdbContainer,
  mdbRow,
  mdbCol,
  mdbColumn,
  mdbBtn,
  mdbIcon,
  mdbModal,
  mdbModalHeader,
  mdbModalBody,
  mdbInput,
  mdbModalFooter
} from "mdbvue";
export default {
  components: {
    Tabla,
    Barnav,
    SelecConcess,
    mdbContainer,
    mdbRow,
    mdbCol,
    mdbColumn,
    mdbBtn,
    mdbIcon,
    mdbModal,
    mdbModalHeader,
    mdbModalBody,
    mdbInput,
    mdbModalFooter
  },
  data() {
    return {
      productos,
      confirm: false,
      value: "",
      cart: false,
      add: [],
      TextName: "",
      LastName: "",
      concess: "",
      direccion: "",
    };
  },
  methods: {
    guardar: function() {
      this.add.push({
        nombre: this.TextName,
        apellido: this.LastName,
        estado: this.estado,
        seleccion: this.concess,
        direc: this.direccion
      });

      this.TextName = "";
      this.LastName = "";
      this.concess = "";
      this.direccion = "";
    },
    BorrarEstado(producto){
    this.productos.splice(producto, 1)
    
      
    },
  
    
  }
};
</script>
<style>
@import url("https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
.table td {
  vertical-align: middle !important;
}
</style>
