<template>
  <div id="app">
    <div class="container mt-5">
      <div class="row">
        <div class="col-md-12">
          <h1 class="text-center font-weight-bolder">PERSONAJES DE RICK Y MORTY</h1>
          <div class="jumbotron">

            <div class="row row-cols-1 row-cols-md-3">

              <div class="col mb-4" v-for="(item, index) of datos" :key="index">
                <div class="card">
                  <img :src="item.image" class="card-img-top" alt="...">
                  <div class="card-body">
                    <h5 class="card-title">{{ item.name }}</h5>
                    <p class="card-text"><b>Genero:</b> {{ item.gender }}</p>
                    <p class="card-text"><b>Especie:</b> {{ item.species }}</p>
                    <p class="card-text"><b>Estado:</b> {{ item.status }}</p>
                    <p class="card-text"><b>Localización:</b> {{ item.location.name }}</p>
                    <p class="card-text"><b>Origen:</b> {{ item.origin.name }}</p>
                  </div>
                </div>
              </div>

            </div>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      datos: {}
    }
  },

  methods: {
    
   api(){  
         this.axios.get('https://rickandmortyapi.com/api/character')
         .then(res => {

           this.datos = res.data.results;

           console.log(this.datos)
         })
         .catch(e => console.log(e))
       }
    
  },

     mounted(){
     this.api()
   }
}
</script>

<style>


</style>