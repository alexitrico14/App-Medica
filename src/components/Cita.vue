<!-- Cita.vue -->
<template>
    <div :style="{ backgroundColor: getColor() }" class="card">
        <p><strong>Paciente:</strong> {{ cita.paciente }}</p>
        <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
        <p><strong>Hora:</strong> {{ cita.hora }}</p>
        <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
        <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
        <button @click="$emit('eliminar-cita')">Eliminar</button>
    </div>
</template>

<script>
export default {
    props: {
        cita: Object
    },
    methods: {
        getColor() {
            switch (this.cita.gravedad) {
                case 'Alta':
                    return 'red';
                case 'Media':
                    return 'yellow';
                default:
                    return 'green';
            }
        }
    }
};
</script>

<style scoped>
.card {
    border: 1px solid #ddd;
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
}
</style>