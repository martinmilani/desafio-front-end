<template>
  <b-container fluid="md" class="d-flex justify-content-center">
    <Reloj :valor="data.valor" :unidad="data.unidad" :nombre="data.nombre" />
  </b-container>
</template>

<script>
import Reloj from "../components/Reloj";
import axios from "axios";

export default {
  components: { Reloj },

  data() {
    return {
      data: {
        nombre: "Presion Directa",
        unidad: "psi",
        valor: "",
      },
    };
  },

  mounted() {
    axios
      .get(
        "http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/presionDirecta"
      )
      .then((response) => (this.data.valor = Object.values(response.data)[0]))
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
