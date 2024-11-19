<template>
  <div class="container mt-4">
    <div class="row">
      <!-- Productos disponibles -->
      <div class="col-lg-6 col-md-6 col-sm-12 mb-4">
        <h3 class="text-center">Productos Disponibles</h3>
        <Productos @agregar="agregarAlCarrito" />
      </div>

      <!-- Carrito de compras -->
      <div class="col-lg-6 col-md-6 col-sm-12 mb-4">
        <h3 class="text-center">Productos en el Carrito</h3>
        <Carrito :carrito="carrito" @remover="removerDelCarrito" />
        <div class="total-container mt-4">
          <h2>Total a Pagar: <strong>${{ totalAPagar.toLocaleString() }}</strong></h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Productos from './Components/Productos.vue';
import Carrito from './Components/Carrito.vue';

export default {
  components: {
    Productos,
    Carrito
  },
  data() {
    return {
      carrito: []
    };
  },
  computed: {
    totalAPagar() {
      return this.carrito.reduce((total, producto) => total + (producto.precio * producto.cantidad), 0);
    }
  },
  methods: {
    agregarAlCarrito(producto) {
      const itemEnCarrito = this.carrito.find(item => item.id === producto.id);
      if (itemEnCarrito) {
        if (itemEnCarrito.cantidad < producto.stock) {
          itemEnCarrito.cantidad++;
        } else {
          alert("No hay más unidades disponibles en stock.");
        }
      } else {
        this.carrito.push({ ...producto, cantidad: 1 });
      }
    },
    removerDelCarrito(index) {
      this.carrito.splice(index, 1);
    }
  }
};
</script>

<style>
body {
  background-color: #f8f9fa;
}

h1 {
  font-size: 2.5em;
  color: #007bff;
}

h3 {
  font-size: 2em;
  color: #333;
}

.total-container h2 {
  font-size: 2em;
  color: #333;
}

</style>

