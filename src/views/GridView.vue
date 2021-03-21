<template>
  <div class="about">
    <b-container>
      <b-row>
        <b-col sm
          ><Reloj
            :valor="datos[0].valor"
            :unidad="datos[0].unidad"
            :nombre="datos[0].nombre"
        /></b-col>
        <b-col sm
          ><Reloj
            :valor="datos[1].valor"
            :unidad="datos[1].unidad"
            :nombre="datos[1].nombre"
        /></b-col>
        <b-col sm
          ><Reloj
            :valor="datos[2].valor"
            :unidad="datos[2].unidad"
            :nombre="datos[2].nombre"
        /></b-col>
      </b-row>
      <b-row>
        <b-col sn
          ><Reloj
            :valor="datos[3].valor"
            :unidad="datos[3].unidad"
            :nombre="datos[3].nombre"
        /></b-col>
        <b-col sm
          ><Reloj
            :valor="datos[4].valor"
            :unidad="datos[4].unidad"
            :nombre="datos[4].nombre"
        /></b-col>
        <b-col sm
          ><Reloj
            :valor="datos[5].valor"
            :unidad="datos[5].unidad"
            :nombre="datos[5].nombre"
        /></b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import Reloj from "../components/Reloj";
import axios from "axios";

export default {
  components: { Reloj },

  data() {
    return {
      datos: [
        { nombre: "Presion Directa", unidad: "psi", valor: "" },
        { nombre: "Presion Anular", unidad: "psi", valor: "" },
        { nombre: "Viento", unidad: "km/h", valor: "" },
        { nombre: "Peso en Gancho", unidad: "kg", valor: "" },
        { nombre: "Peso Aplicado", unidad: "kg", valor: "" },
        { nombre: "Nivel Pileta", unidad: "mts", valor: "" },
      ],
    };
  },

  mounted() {
    axios
      .get(
        "http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/presionDirecta"
      )
      .then(
        (response) => (this.datos[0].valor = Object.values(response.data)[0])
      )
      .catch((error) => {
        console.log(error);
      });

    axios
      .get(
        "http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/presionAnular"
      )
      .then(
        (response) => (this.datos[1].valor = Object.values(response.data)[0])
      )
      .catch((error) => {
        console.log(error);
      });

    axios
      .get("http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/viento")
      .then(
        (response) => (this.datos[2].valor = Object.values(response.data)[0])
      )
      .catch((error) => {
        console.log(error);
      });

    axios
      .get(
        "http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/pesoEnGancho"
      )
      .then(
        (response) => (this.datos[3].valor = Object.values(response.data)[0])
      )
      .catch((error) => {
        console.log(error);
      });

    axios
      .get(
        "http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/pesoAplicado"
      )
      .then(
        (response) => (this.datos[4].valor = Object.values(response.data)[0])
      )
      .catch((error) => {
        console.log(error);
      });

    axios
      .get(
        "http://api.tenlek.com/a70da940ce76c1217f03376a3ac725fc/nivelPileta "
      )
      .then(
        (response) => (this.datos[5].valor = Object.values(response.data)[0])
      )
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
