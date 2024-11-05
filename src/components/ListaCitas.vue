<!-- ListaCitas.vue -->
<template>
    <div v-if="citas.length > 0">
      <Cita
        v-for="(cita, index) in citas"
        :key="index"
        :cita="cita"
        @eliminar-cita="eliminarCita(index)"
      />
    </div>
    <p v-else>Aún no hay consultas registradas.</p>
  </template>
  
  <script>
  import Cita from './Cita.vue';
  
  export default {
    components: { Cita },
    props: {
      citas: Array
    },
    methods: {
      eliminarCita(index) {
        this.$emit('eliminar-cita', index);
      }
    }
  };
  </script>
  