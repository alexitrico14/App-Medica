<script>
import FormularioCita from './components/FormularioCita.vue';
import ListaCitas from './components/ListaCitas.vue';

export default {
  name: 'App',
  components: {
    FormularioCita,
    ListaCitas
  },
  data() {
    return {
      citas: []
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    }
  }
};
</script>

<template>
  <div id="app">
    <h1>Administrador de Citas Médicas</h1>
    <FormularioCita @nueva-cita="agregarCita" />
    <ListaCitas :citas="citas" @eliminar-cita="eliminarCita" />
  </div>
</template>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  text-align: center;
  color: #007bff;
  font-size: 24px;
  margin-bottom: 20px;
}
</style>
