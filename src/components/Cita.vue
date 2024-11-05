<script>
export default {
    props: ['cita'],
    methods: {
        getColor() {
            if (this.cita.gravedad === 'Alta') return '#f8d7da';
            if (this.cita.gravedad === 'Media') return '#fff3cd';
            return '#d4edda';
        }
    }
};
</script>

<template>
    <div :style="{ backgroundColor: getColor() }" class="card">
        <p><strong>Paciente:</strong> {{ cita.paciente }}</p>
        <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
        <p><strong>Hora:</strong> {{ cita.hora }}</p>
        <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
        <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
        <button @click="$emit('eliminar-cita')" class="btn-eliminar">Eliminar</button>
    </div>
</template>

<style scoped>
.card {
    border: 1px solid #ddd;
    padding: 15px;
    margin: 10px 0;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    color: #333;
}

.card p {
    margin: 5px 0;
}

.btn-eliminar {
    padding: 5px 10px;
    background-color: #dc3545;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.btn-eliminar:hover {
    background-color: #c82333;
}
</style>