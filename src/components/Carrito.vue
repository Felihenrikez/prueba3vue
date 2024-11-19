<template>
  <div class="carrito">
    <div v-for="(producto, index) in carrito" :key="producto.id" class="producto-en-carrito">
      <img :src="`/images/${producto.imagen}`" alt="producto" class="producto-imagen" />
      <div class="producto-info">
        <h5>{{ producto.nombre }}</h5>
        <p>Cantidad: {{ producto.cantidad }}</p>
        <p>Precio: ${{ (producto.precio * producto.cantidad).toLocaleString() }}</p>
        <button @click="removerDelCarrito(index)" class="btn btn-danger btn-sm">Eliminar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['carrito'],
  methods: {
    removerDelCarrito(index) {
      this.$emit('remover', index);
    }
  }
};
</script>

<style scoped>
.carrito {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.producto-en-carrito {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 8px;
}

.producto-imagen {
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 8px;
}

.producto-info {
  flex-grow: 1;
}

button {
  margin-top: 5px;
}
</style>
