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
            const nuevaCita = {
                paciente: this.paciente,
                fecha: this.fecha,
                hora: this.hora,
                gravedad: this.gravedad,
                motivo: this.motivo
            };
            this.$emit('nueva-cita', nuevaCita);
            this.paciente = '';
            this.fecha = '';
            this.hora = '';
            this.gravedad = '';
            this.motivo = '';
        }
    }
};
</script>

<template>
    <form @submit.prevent="enviarCita" class="formulario-cita">
        <div class="campo">
            <label :style="{ color: paciente === '' ? 'red' : 'black' }">Paciente:</label>
            <input type="text" v-model="paciente" />
        </div>
        <div class="campo">
            <label :style="{ color: fecha === '' ? 'red' : 'black' }">Fecha:</label>
            <input type="date" v-model="fecha" />
        </div>
        <div class="campo">
            <label :style="{ color: hora === '' ? 'red' : 'black' }">Hora:</label>
            <input type="time" v-model="hora" />
        </div>
        <div class="campo">
            <label :style="{ color: gravedad === '' ? 'red' : 'black' }">Gravedad:</label>
            <select v-model="gravedad">
                <option disabled value="">Seleccione</option>
                <option value="Baja">Baja</option>
                <option value="Media">Media</option>
                <option value="Alta">Alta</option>
            </select>
        </div>
        <div class="campo">
            <label :style="{ color: motivo === '' ? 'red' : 'black' }">Motivo:</label>
            <textarea v-model="motivo"></textarea>
        </div>
        <button :disabled="!paciente || !fecha || !hora || !gravedad || !motivo" class="btn-agregar">Agregar
            Cita</button>
    </form>
</template>

<style scoped>
.formulario-cita {
    display: flex;
    flex-direction: column;
    gap: 15px;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
    background-color: #f9f9f9;
    margin-bottom: 20px;
}

.campo label {
    font-weight: bold;
    display: block;
    margin-bottom: 5px;
}

.campo input,
.campo select,
.campo textarea {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.btn-agregar {
    padding: 10px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
}

.btn-agregar:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}
</style>