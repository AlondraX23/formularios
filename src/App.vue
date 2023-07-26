<script setup>
import { ref } from 'vue'


const registro = ref({
  nombre: '',
  apellido: '',
  sexo: '',
  edad: '',
  correo: '',
  password: '',
  conociminto: [],
  admin: false,
  observaciones: '',
  grupo: ''
})
console.log(registro)

const guardar = (event) => {
  // event.preventDefault()
  console.log(registro.value)
  mostrarInicio = true;
  mostrarRegistro = false
}

var mostrarInicio = false
var mostrarRegistro = true


// function guardar(){
//   mostrarInicio = true;
//   mostrarRegistro = false
// }

function irRegistro(){
  mostrarRegistro = true
  mostrarInicio = false;

}

var passwordI = ref("");
var correoI = ref("");


function ingresar(registro) {
  if((passwordI.value === registro.password) && (correoI.value === registro.correo)){
    alert("yes")
  } else{
    alert("no")
  }
  console.log(passwordI)
  console.log(correoI)
  // console.log(registro.password)
}





</script>

<template>
  <nav class="navbar bg-body-tertiary" data-bs-theme="dark">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img src="src/assets/logo.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
        Bootstrap
      </a>
    </div>
  </nav>
  <div class="container py-4 ">
    <h1>Registro</h1>
    <form v-show="mostrarRegistro" class="card p-4 bg-success bg-opacity-25  border-0">
      <div class="row mb-3">
        <label for="nombre" class="col-sm-2 col-form-label">Nombre</label>
        <div class="col-sm-10">
          <input type="text" class="form-control border border-success-subtle" id="nombre" v-model="registro.nombre">
        </div>
      </div>
      <div class="row mb-3">
        <label for="apellido" class="col-sm-2 col-form-label">Apellido</label>
        <div class="col-sm-10">
          <input type="text" class="form-control border border-success-subtle" id="apellido" v-model="registro.apellido">
        </div>
      </div>

      <fieldset class="row mb-3">
        <legend class="col-form-label col-sm-2 pt-0">Sexo</legend>
        <div class="col-sm-10">
          <div class="form-check">
            <input class="form-check-input" type="radio" name="sexo" id="sexo-F" value="F" v-model="registro.sexo">
            <label class="form-check-label" for="sexo-F">
              Femenino
            </label>
          </div>
          <div class="form-check">
            <input class="form-check-input" type="radio" name="sexo" id="sexo-M" value="M">
            <label class="form-check-label" for="sexo-M">
              Masculino
            </label>
          </div>
        </div>
      </fieldset>

      <div class="row mb-3">
        <label for="edad" class="col-sm-2 col-form-label">Edad</label>
        <div class="col-sm-10">
          <input type="number" class="form-control border border-success-subtle" id="edad" v-model="registro.edad">
        </div>
      </div>

      <div class="row mb-3">
        <label for="correo" class="col-sm-2 col-form-label">Correo</label>
        <div class="col-sm-10">
          <input type="email" class="form-control" id="correo" v-model="registro.correo">
        </div>
      </div>
      <div class="row mb-3">
        <label for="password" class="col-sm-2 col-form-label">Contraseña</label>
        <div class="col-sm-10">
          <input type="password" class="form-control" id="password" v-model="registro.password">
        </div>
      </div>

      <fieldset class="row mb-3">
        <legend class="col-form-label col-sm-2 pt-0">Conocimientos</legend>
        <div class="col-sm-10">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="HTML" v-model="registro.conociminto">
            <label class="form-check-label" for="HTML">
              HTML
            </label>
          </div>

          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="CSS" v-model="registro.conociminto">
            <label class="form-check-label" for="CSS">
              CSS
            </label>
          </div>

          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="JS" v-model="registro.conociminto">
            <label class="form-check-label" for="JS">
              JavaScript
            </label>
          </div>
        </div>
      </fieldset>

      <div class="row mb-3">
        <div class="col-sm-10 offset-sm-2">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="admin" v-model="registro.admin">
            <label class="form-check-label" for="admin">
              ¿Usuario admin?
            </label>
          </div>
        </div>
      </div>

      <div class="form-floating pb-4">
        <textarea class="form-control" placeholder="Leave a comment here" id="observaciones" style="height: 100px"
          v-model="registro.observaciones"></textarea>
        <label for="observaciones">Comments</label>
      </div>

      <fieldset class="row mb-3">
        <legend class="col-form-label col-sm-2 pt-0">Grupo</legend>
        <div class="col-sm-10">
          <select id="grupo" v-model="registro.grupo" class="form-select" aria-label="Default select example">
            <option selected>...</option>
            <optgroup label="Sección 1">
              <option value="A">A</option>
              <option value="B">B</option>
              <option value="C">C</option>
            </optgroup>
            <optgroup label="Sección 1">
              <option value="D">D</option>
              <option value="E">E</option>
              <option value="F">F</option>
            </optgroup>
          </select>
        </div>
      </fieldset>


      <div class="d-grid gap-2 d-md-flex justify-content-md-end">
        <button type="submit" class="btn btn-primary" @click="guardar">Guardar</button>
        <button type="reset" class="btn btn-outline-danger">Borrar</button>
      </div>
    </form>

    <div v-show="mostrarInicio">
      <form class="card p-4 bg-success bg-opacity-25  border-0">
        <div class="row mb-3">
        <label for="correoI" class="col-sm-2 col-form-label">Correo</label>
        <div class="col-sm-10">
          <input type="email" class="form-control" id="correoI" v-model="correoI">
        </div>
      </div>
      <div class="row mb-3">
        <label for="passwordI" class="col-sm-2 col-form-label">Contraseña</label>
        <div class="col-sm-10">
          <input type="password" class="form-control" id="passwordI" v-model="passwordI">
        </div>
      </div>

      <div class="d-grid gap-2 d-md-flex justify-content-md-end">
        <button type="submit" class="btn btn-primary" @click="ingresar">Ingresar</button>
        <button type="button" class="btn btn-outline-warning" @click="irRegistro = true">registro</button>
      </div>

      </form>

    </div>
  </div>

  <footer class=" bg-body-tertiary text-white" data-bs-theme="dark">
    <div class="container-fluid py-3">
      <a class="navbar-brand" href="#">
        <img src="src/assets/logo.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
        Bootstrap
      </a>
    </div>
  </footer>
</template>