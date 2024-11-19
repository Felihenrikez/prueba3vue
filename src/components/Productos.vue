<template> 
  <div class="productos">
    <div v-for="producto in productos" :key="producto.id" class="producto-card">
      <img :src="`/images/${producto.imagen}`" alt="producto" class="producto-imagen" />
      <div class="producto-info">
        <h5>{{ producto.nombre }}</h5>
        <p>Precio: ${{ producto.precio.toLocaleString() }}</p>
        <button @click="agregarProducto(producto)" class="btn btn-primary">
          <i class="fa fa-shopping-cart"></i>
           Agregar al carrito
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      productos: [
        { id: 1, nombre: 'Teclado', precio: 15000, imagen: 'teclado.jpg', stock: 10 },
        { id: 2, nombre: 'Mouse', precio: 20000, imagen: 'mouse.jpg', stock: 5 },
        { id: 3, nombre: 'Gabinete', precio: 35000, imagen: 'gabinete.jpg', stock: 4 },
        { id: 4, nombre: 'Audifono', precio: 30000, imagen: 'audifono.jpg', stock: 3 },
        { id: 5, nombre: 'Pantalla', precio: 175000, imagen: 'pantalla.jpg', stock: 3 },
        { id: 6, nombre: 'Silla', precio: 150000, imagen: 'silla.jpg', stock: 2 }
      ]
    };
  },
  methods: {
    agregarProducto(producto) {
      this.$emit('agregar', producto);
    }
  }
};
</script>

<style scoped>
.producto-card {
  margin-bottom: 5px;
  text-align: left; 
  width: 200px;
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  display: flex; 
  flex-direction: row; 
  gap: 10px; 
}

.producto-imagen {
  width: 40%; 
  height: 100px;
  object-fit: cover;
  border-radius: 8px;
}

.producto-info {
  display: flex;
  flex-direction: column; 
  justify-content: space-between; 
  flex-grow: 1;
}

.producto-info h5,
.producto-info p {
  margin: 0; 
}

/* Botón de agregar al carrito */
.producto-info button {
  display: flex;
  align-items: center; /* Centra la imagen y el texto verticalmente */
  justify-content: center; /* Centra todo el contenido en el botón */
  font-size: 0.8em;
  padding: 5px 15px;
  border-radius: 5px;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
}

.producto-info button i {
  margin-right: 8px; /* Espacio entre el ícono y el texto */
  font-size: 1.2em; /* Ajusta el tamaño del ícono */
}

</style>
