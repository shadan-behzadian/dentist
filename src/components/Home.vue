<template>
  <div>
    <input type="text" v-model="search" />
    <table>
      <thead>
        <tr>
          <th>Nombre y apellidos</th>
          <th>Clinica</th>
          <th>Objetivo Tratamiento</th>
          <th>Estado</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(paciente, id) in pacientes"
          v-bind:key="id"
          @click="(showModal = true), selectPatient(paciente)"
        >
          <td>
            {{ paciente.datos_paciente.nombre }}
            {{ paciente.datos_paciente.apellidos }}
          </td>
          <td>
            {{ paciente.ficha_dental.clinica }}
          </td>
          <td>{{ paciente.ficha_dental.objetivo_tratamiento }}</td>

          <td>{{ paciente.ficha_dental.estado }}</td>
          <td>
            <select name="Acciones" id="Acciones">
              <option value="" disabled selected>Acciones</option>
              <option value="Editar">Editar</option>
              <option value="Finalizar">Finalizar</option>
              <option value="Borrar">Borrar</option>
            </select>
          </td>
        </tr>
      </tbody>
    </table>

    <!-- <div>{{ search }}</div> -->
    <!-- use the modal component, pass in the prop -->
    <modal
      v-if="showModal"
      @close="showModal = false"
      v-bind:selectedPatient="selectedPatient"
    >
    </modal>
  </div>
</template>

<script>
import FichaModal from "./FichaModal.vue";
// import NewPatient from "../components/NewPatient.vue";
export default {
  name: "Home",
  components: {
    modal: FichaModal,
    // newPatient: NewPatient,
  },
  data() {
    return {
      showModal: false,
      selectedPatient: {},
      search: "",
    };
  },

  props: {
    pacientes: { type: Object, required: true },
  },
  methods: {
    selectPatient(paciente) {
      this.selectedPatient = paciente;
    },
  },
  // computed: {
  //   filterdPatient: function() {
  //     return this.pacientes.filter((paciente) => {
  //       return paciente.datos_paciente.nombre
  //         .toLowerCase()
  //         .includes(this.search.toLowerCase());
  //     });
  //   },
  // },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
    width: 100%;
    display: table;
    border-collapse: collapse;
    border-spacing: 0;
}


element.style {
}
table {
    width: 100%;
    display: table;
    border-collapse: collapse;
    border-spacing: 0;
}
table, th, td {
    border: none;
}

</style>
