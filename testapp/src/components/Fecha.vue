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
          <p class="fs-4">Cual es tu fecha de nacimiento?</p>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Dia"
              v-model="datos.dia"
              v-on:keyup="emitFecha()"
            />
          </div>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Mes"
              v-model="datos.mes"
              v-on:keyup="emitFecha()"
            />
          </div>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Año"
              v-model="datos.anio"
              v-on:keyup="emitFecha()"
            />
          </div>
        </div>
      </div>
      <div
        class="alert pink"
        role="alert"
        v-if="datos.dia != '' || datos.mes != '' || datos.anio != ''">
        {{datos.dia +" " +datos.mes +" " +datos.anio}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Fecha",
  data() {
    return {
        datos:  {
            dia: "",
            mes: "",
            anio: "",
        },
    }
  },
  methods: {
      emitFecha(){
          this.$emit('fecha', this.datos)
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
