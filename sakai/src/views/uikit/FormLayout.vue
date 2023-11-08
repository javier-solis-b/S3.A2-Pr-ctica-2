<template>
  <div class="grid">
    <div class="col-12 md:12">
      <div class="card p-fluid">
        <div class="card-body">
          <h4 class="card-title">Lista de Platillos</h4>
          <div class="table-responsive">
            <table class="table table-bordered">
              <thead>
                <tr>
                  <th>Nombre</th>
                  <th>Descripción</th>
                  <th>Precio</th>
                  <th>Acciones</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="platillo in platillos" :key="platillo.id">
                  <td>{{ platillo.nombre }}</td>
                  <td>{{ platillo.descripcion }}</td>
                  <td>{{ formatCurrency(platillo.precio) }}</td>
                  <td>
                    <button class="btn btn-primary" @click="editarPlatillo(platillo)">Editar</button>
                    <button class="btn btn-danger" @click="eliminarPlatillo(platillo)">Eliminar</button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
        <div class="card-footer">
          <button class="btn btn-success" @click="agregarPlatillo">Agregar Platillo</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const platillos = ref([
  { id: 1, nombre: 'Platillo 1', descripcion: 'Descripción del Platillo 1', precio: 10.99 },
  { id: 2, nombre: 'Platillo 2', descripcion: 'Descripción del Platillo 2', precio: 15.99 },
  { id: 3, nombre: 'Platillo 3', descripcion: 'Descripción del Platillo 3', precio: 8.99 },
]);

const formatCurrency = (value) => {
  return value.toLocaleString('en-US', { style: 'currency', currency: 'USD' });
};

const agregarPlatillo = () => {
  // Lógica para agregar un nuevo platillo a la lista
};

const editarPlatillo = (platillo) => {
  // Lógica para editar un platillo
};

const eliminarPlatillo = (platillo) => {
  // Lógica para eliminar un platillo
};
</script>

