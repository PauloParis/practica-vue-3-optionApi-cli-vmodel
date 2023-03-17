<template>
  <main>
    <form @submit.prevent="procesarFormulario">
      <input 
        type="text"
        class="form-control my-2"
        placeholder="Ingrese Nombre"
        v-model.trim="tarea.nombre"
      >
      <div class="form-check form-check-inline">
        <input 
          type="checkbox" 
          id="check-1" 
          class="form-check-input"
          v-model="tarea.categorias"
          value="Javascript"
        >
        <label 
          for="check-1" 
          class="form-check-label"
        >Javascript</label>
      </div>
      <div class="form-check form-check-inline">
        <input 
          type="checkbox" 
          id="check-2" 
          class="form-check-input"
          v-model="tarea.categorias"
          value="Nodejs"
        >
        <label 
          for="check-2" 
          class="form-check-label"
        >node js</label>
      </div>

      <div class="mt-2">
        <div class="form-check form-check-inline">
          <input 
            type="radio"
            id="radio-1" 
            class="form-check-input"
            v-model="tarea.estado"
            value="urgente"
          >
          <label for="radio-1" class="form-check-label">Urgente</label>
        </div>
      </div>
      <div class="mt-2">
        <div class="form-check form-check-inline">
          <input 
            type="radio"
            id="radio-2" 
            class="form-check-input"
            v-model="tarea.estado"
            value="relax"
          >
          <label for="radio-2" class="form-check-label">Relax</label>
        </div>
      </div>
      <div class="mt-2">
        <input 
          type="text"
          class="form-control"
          v-model.number="tarea.numero"
        >
      </div>
      <button 
        class="mt-2 btn btn-dark w-100"
        :disabled="bloquear"
      >Procesar</button>
    </form>
  </main>
</template>


<script>

export default {
  data(){
    return {
      tarea: {
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  methods: {
    procesarFormulario(){
      console.log(this.tarea)
      if(this.tarea.nombre.trim() === ''){
        console.log('Campo vacio')
        return
      }
      console.log('No esta vacio')
      this.tarea = {
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  computed: {
    bloquear(){
      return this.tarea.nombre.trim() === '' ? true : false
    }
  }
}

</script>