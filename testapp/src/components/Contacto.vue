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
          <p class="fs-4">Datos de Contacto</p>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Correo Electronico"
              v-model="datos.correo"
              v-on:keyup="emitContacto()"
            />
          </div>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Numero de Celular"
              v-model="datos.celular"
              v-on:keyup="emitContacto()"
            />
          </div>
        </div>
      </div>
      <div class="alert pink" role="alert" v-if="datos.correo != '' || datos.celular != ''">
        <h6>{{ "Correo Electronico: " + datos.correo }}</h6>
        <h6>{{ "Numero de Celular: " + datos.celular }}</h6>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Contacto",
  data() {
    return {
      datos: {
        correo: "",
        celular: "",
      },
    }
  },
  methods: {
      emitContacto(){
          this.$emit('contacto', this.datos)
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
