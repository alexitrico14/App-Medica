<script>
import Cita from './Cita.vue';

export default {
  props: ['citas'],
  components: {
    Cita
  },
  methods: {
    eliminarCita(index) {
      this.$emit('eliminar-cita', index);
    }
  }
};
</script>

<template>
  <div class="lista-citas" v-if="citas.length > 0">
    <Cita v-for="(cita, index) in citas" :key="index" :cita="cita" @eliminar-cita="eliminarCita(index)" />
  </div>
  <p v-else class="mensaje-vacio">Aún no hay consultas registradas.</p>
</template>

<style scoped>
.lista-citas {
  margin-top: 20px;
}

.mensaje-vacio {
  text-align: center;
  font-style: italic;
  color: #666;
}
</style>