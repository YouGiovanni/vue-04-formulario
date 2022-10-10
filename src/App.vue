<script>
import ProgressBar from './ProgressBar.vue';
import TotalProyectos from './assets/components/TotalProyectos.vue';
export default {
    data: () => ({
        proyecto: "",
        tipo: "",   //String 
        urgente: false, //boolean true y false
        proyectos: [],  //arreglo
    }),
    methods: {
        registrarProyecto() {
            const proyecto = {
                proyecto: this.proyecto,
                tipo: this.tipo,
                urgente: this.urgente,
                completado: false,
            };
            this.proyectos.push(proyecto);
            this.proyecto = "";
            this.tipo = "";
            this.urgente = false;
        },
        cambiarEstado(proyecto, campo) {
            //this.proyectos[id].urgente = !this.proyectos[id].urgente;
            //console.log(proyecto, campo);
            proyecto[campo] = !proyecto[campo];
        },
    },
    computed: {
        numeroProyectos() {
            return this.proyectos.length;
        },
        porcentaje() {
            let completados = 0;
            this.proyectos.map(proyecto => {
                if (proyecto.completado)
                    completados++;
            });
            return (completados * 100) / this.numeroProyectos || 0;
        }
    },
    components: { ProgressBar, TotalProyectos }
};
</script>

<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous" />

  <h1>Formularios</h1>
  <img src="https://cdn.svgporn.com/logos/vue.svg" alt="" width="120" height="120" />
  <h2>Alumno: Valencia Vazquez You Giovanni</h2>

  <div class="row">
    <div class="col-12 mb-4">
      <progress-bar/>
    </div>
    <div class="col-12 col-md-4">
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
            <option>Backend Services Node.js</option>
            <option>App movil con ReactNative</option>
          </select>
        </div>

        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-check-label">Urgente</label>
          <input v-model="urgente" type="checkbox" class="form-check-input" />
        </div>
        <button type="submit" class="btn btn-primary">Guardar</button>
      </form>
    </div>
    <div class="col-12 col-md-8">
      <total-proyectos :numeroProyectos="numeroProyectos" :proyectos="proyectos" :cambiarEstado="cambiarEstado"/>
      <hr />
    </div>
  </div>
</template>
