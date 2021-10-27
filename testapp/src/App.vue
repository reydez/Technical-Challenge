<template>
  <div id="app">
    <head>
      <meta name="viewport" content="width=device-width, inicial-scale=1" />
      <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.6.1/font/bootstrap-icons.css">
    </head>
    <nav class="navbar navbar-expand-sm py-5 pink">
      <div class="container">
        <div class="row row-cols-2">
          <div class="col"><h6>Titulo de formulario</h6></div>
          <div class="col"><i class="bi bi-clipboard bi-3x"></i></div>
          <div class="col"><i class="bi-alarm">En menos de 5 minutos</i></div>
        </div>
        <!--<ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link active letrasColor">Titulo del Formulario</a>
          </li>
        </ul>-->
      </div>
    </nav>

    <Nombre v-on:nombre="getNombre($event)" />
    <Fecha v-on:fecha="getFecha($event)" />
    <Contacto v-on:contacto="getContacto($event)" />

    <div class="alert border ms-5 me-2 mt-2 bgContenedor">
      Si tus datos son correctos por favor continuemos
    </div>

    <div class="d-grid gap-2 col-9 m-2 mx-auto">
      <button class="btn pink" v-on:click="iniciar()" type="button">
        Iniciar
      </button>
    </div>

    <div class="alert border m-2 pink" v-if="bandera" ref="contenedor">
      <h6>{{ fecha_de_nacimeinto }}</h6>
      <h6>{{ correo_electronico }}</h6>
      <h6>{{ telefono_celular }}</h6>
      <h6>{{ nombre }}</h6>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap/dist/js/bootstrap.min.js";

import Nombre from "./components/Nombre.vue";
import Fecha from "./components/Fecha.vue";
import Contacto from "./components/Contacto.vue";

export default {
  name: "App",
  data() {
    return {
      nombre_completo: "",
      fecha_completa: "",
      contacto_completo: "",
      fecha_de_nacimeinto: "",
      correo_electronico: "",
      telefono_celular: "",
      nombre: "",
      bandera: false,
    };
  },
  mounted() {
    window.scrollTo(document.body.scrollHeight, 0);
  },
  components: {
    Nombre,
    Fecha,
    Contacto,
  },
  methods: {
    getNombre(nombre_completo) {
      this.nombre_completo = nombre_completo;
    },
    getFecha(fecha_completa) {
      this.fecha_completa = fecha_completa;
    },
    getContacto(contacto_completo) {
      this.contacto_completo = contacto_completo;
    },
    iniciar() {
      if (
        this.nombre_completo != "" ||
        this.fecha_completa != "" ||
        this.contacto_completo != ""
      ) {
        if (
          this.nombre_completo.nombre == "" ||
          this.nombre_completo.segundo_nombre == "" ||
          this.nombre_completo.apellido_paterno == "" ||
          this.nombre_completo.apellido_materno == "" ||
          this.fecha_completa.dia == "" ||
          this.fecha_completa.mes == "" ||
          this.fecha_completa.anio == "" ||
          this.contacto_completo.correo == "" ||
          this.contacto_completo.celular == ""
        ) {
          alert("algunos campos estan vacios");
        } else {
          this.bandera = true;
          this.fecha_de_nacimeinto =
            "Fecha de nacimiento: " +
            this.fecha_completa.dia +
            " " +
            this.fecha_completa.mes +
            " " +
            this.fecha_completa.anio;
          this.correo_electronico =
            "Correo electrónico: " + this.contacto_completo.correo;
          this.telefono_celular =
            "Telefono celular: " + this.contacto_completo.celular;
          this.nombre =
            "Nombre: " +
            this.nombre_completo.nombre +
            " " +
            this.nombre_completo.segundo_nombre +
            " " +
            this.nombre_completo.apellido_paterno +
            " " +
            this.nombre_completo.apellido_materno;

          setTimeout(function () {
            window.scrollTo(0, document.body.scrollHeight);
          }, 100);
        }
      } else {
        alert("algunos campos estan vacios");
      }
    },
  },
};
</script>
<style>
.pink {
  background: palevioletred;
}

.bgContenedor {
  background: #eeeeee;
}

.letrasColor {
  color: black;
  font-size: 12px;
}
</style>
