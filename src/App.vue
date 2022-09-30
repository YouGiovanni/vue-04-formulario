<script>
export default {
  data: () => ({
    proyecto: "",
    tipo: "",
    urgente: false,
    proyectos: [],
  }),
  methods: {
    registrarProyecto() {
      const proyecto = {
        proyecto: this.proyecto,
        tipo: this.tipo,
        urgente: this.urgente,
      };

      this.proyectos.push(proyecto);
      console.log(this.proyectos);

      this.proyecto = "";
      this.tipo = "";
      this.urgente = "";
    },
  },
};
</script>

<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

  <div class="col-12 ">
    <h1>Formularios</h1>
    <img src="https://cdn.svgporn.com/logos/vue.svg" :alt="alt" width="100">
  </div>

  <hr/>

  <h2>Alumno: Valencia Vazquez You Giovanni</h2>

  <form @submit.prevent="registrarProyecto">
    <div class="mb-3">
      <label class="form-label">Proyecto</label>
      <input v-model.trim="proyecto" type="text" class="form-control" required />
    </div>

    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Actividad</label>
      <select v-model.trim="tipo" class="form-select" required>
        <option disabled selected value="Selecciona un tipo ..."></option>
        <option>Aplicaciones Web con Vue.js</option>
        <option> Backend Services Node.js </option>
        <option>App movil con ReactNative </option>
      </select>
    </div>

    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-check-label">Urgente</label>
      <input v-model="urgente" type="checkbox" class="form-check-input" />
    </div>
    <button type="submit" class="btn btn-primary">Guardar</button>
  </form>

  <hr>

  <div class="table-responsive">
    <table class="table table-dark">
      <thead>
        <tr>
          <th>#</th>
          <th>Proyecto</th>
          <th>Tipo</th>
          <th>Urgente</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <td>1</td>
          <td>Laravel app</td>
          <td>Larabel</td>
          <td class="bg-success">Si/No</td>
        </tr>
      </tbody>
    </table>
  </div>


</template>
 
<style scoped>
.div {
  text-align: center;
  align-items: center;
}
h1{
  text-align: left;
}

img{
  align-items: flex-end;
}
</style>