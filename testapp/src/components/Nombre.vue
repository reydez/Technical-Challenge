<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-auto mt-2">
          <img
            src="//placehold.it/100"
            class="img-fluid rounded-circle"
            alt=""
          />
        </div>
        <div class="col rounded m-2 bgContenedor">
          <p class="fs-4">Cual es tu nombre?</p>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Nombre"
              v-model="datos.nombre"
              v-on:keyup="emitNombre()"
            />
          </div>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Segundo Nombre"
              v-model="datos.segundo_nombre"
              v-on:keyup="emitNombre()"
            />
          </div>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Apellido Paterno"
              v-model="datos.apellido_paterno"
              v-on:keyup="emitNombre()"
            />
          </div>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Apellido Materno"
              v-model="datos.apellido_materno"
              v-on:keyup="emitNombre()"
            />
          </div>
        </div>
      </div>
      <div
        class="alert pink"
        role="alert"
        v-if="datos.nombre != '' ||datos.segundo_nombre != '' ||datos.apellido_paterno != '' ||datos.apellido_materno != ''">
        {{datos.nombre +" " + datos.segundo_nombre +" " +datos.apellido_paterno +" " +datos.apellido_materno}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nombre",
  data() {
    return {
        datos:  {
            nombre: "",
            segundo_nombre: "",
            apellido_paterno: "",
            apellido_materno: "",
        },
    }
  },
  methods: {
      emitNombre(){
          this.$emit('nombre', this.datos)
      }
  }
};
</script>
<style scoped>
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
