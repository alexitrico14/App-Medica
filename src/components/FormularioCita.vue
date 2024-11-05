<!-- FormularioCita.vue -->
<template>
    <form @submit.prevent="enviarCita">
        <div>
            <label :style="{ color: paciente === '' ? 'red' : 'black' }">Paciente:</label>
            <input type="text" v-model="paciente" />
        </div>
        <div>
            <label :style="{ color: fecha === '' ? 'red' : 'black' }">Fecha:</label>
            <input type="date" v-model="fecha" />
        </div>
        <div>
            <label :style="{ color: hora === '' ? 'red' : 'black' }">Hora:</label>
            <input type="time" v-model="hora" />
        </div>
        <div>
            <label :style="{ color: gravedad === '' ? 'red' : 'black' }">Gravedad:</label>
            <select v-model="gravedad">
                <option disabled value="">Seleccione</option>
                <option value="Baja">Baja</option>
                <option value="Media">Media</option>
                <option value="Alta">Alta</option>
            </select>
        </div>
        <div>
            <label :style="{ color: motivo === '' ? 'red' : 'black' }">Motivo:</label>
            <textarea v-model="motivo"></textarea>
        </div>
        <button :disabled="!paciente || !fecha || !hora || !gravedad || !motivo">Agregar Cita</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            paciente: '',
            fecha: '',
            hora: '',
            gravedad: '',
            motivo: ''
        };
    },
    methods: {
        enviarCita() {
            this.$emit('nueva-cita', {
                paciente: this.paciente,
                fecha: this.fecha,
                hora: this.hora,
                gravedad: this.gravedad,
                motivo: this.motivo
            });
            this.limpiarFormulario();
        },
        limpiarFormulario() {
            this.paciente = '';
            this.fecha = '';
            this.hora = '';
            this.gravedad = '';
            this.motivo = '';
        }
    }
};
</script>