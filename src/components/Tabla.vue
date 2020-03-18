<template>
  <tr>
    <td>{{producto.id}}</td>
    <td>{{producto.nombre}}</td>
    <td>{{producto.apellido}}</td>
    <td>{{producto.direccion}}</td>
    <td >{{producto.status}}</td>
    <td>{{producto.asignado}}</td>
    <td>
      <div>
        <a
          href="#"
          role="button"
          v-on:click="BorrarEstado(producto)"
          class="btn btn-outline-dark btn-sm"
        >
          <i class="fas fa-trash-alt fa-2x" style="color:DodgerBlue"></i>
        </a>
        <a href="#" role="button" type="button"
        v-on:click="EditaEstado(producto.status)"
         class="btn btn-outline-dark btn-sm">
          <i class="fas fa-user-edit fa-2x" style="color:DodgerBlue"></i>
        </a>
      </div>
    </td>
  </tr>
</template>

<script>
export default {
  name: "Tabla",
  props: ['producto'],
  data(){
    return{
      cambiaEstado:'inactivo'
    }
  },
  methods:{
    BorrarEstado:function(producto){
        this.$emit('borrar-item',producto)
     
    }

  }
};
</script>

<style>
</style>