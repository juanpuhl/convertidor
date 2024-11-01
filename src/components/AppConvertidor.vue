<template>
  <div class="container pt-3">
    <h5></h5>
    <div class="row">
      <div class="col-lg-12">
            <div class="form-group">
              <label for="cantidad" class="form-label text-white">Ingrese cantidad</label>
              <input type="number" class="form-control form-control-lg" 
                    v-model="cantidad"
                    v-on:keyup="convertirMoneda"
                    id="cantidad" placeholder="Ingrese cantidad...">
            
          </div>

      </div>
      <div class="row">
        <div class="col-lg-6">
                    <div class="form-group" > 
                      <label for="tengo">Tengo</label>
                      <select class="form-control form-control-lg" id="tengo" v-model="tengo"
                      v-on:change="convertirMoneda">
                          <option v-for="(moneda, index) in monedas" v-bind:key="index">{{moneda}}</option>
                          
                      </select>
                    </div>
        </div>
        <div class="col-lg-6">
          <div class="form-group" > 
                      <label for="quiero">Quiero</label>
                      <select class="form-control form-control-lg" id="quiero" v-model="quiero"
                      v-on:change="convertirMoneda">
                        <option v-for="(moneda, index) in monedas" v-bind:key="index">{{moneda}}</option>
                      </select>
                    </div>
        </div>
      </div>
      <div class="text-center pt-3">
        <h5>
          <span class="badge bg-success" >{{cantidad}} {{tengo}}</span>
          <span class="badge bg-dark" >SON </span>
          <!-- este metodo es para redondear pero no me gusta como lo hace{{getTotal(total)}}-->
          <span class="badge bg-success" > {{ total }} {{quiero}}</span>
        </h5>
      </div>

    </div>
  </div>
    
  </template>
  
  <script>
   export default {
    name: 'App',
    components: {  
    },
    data(){
        return{
          monedas: ['USD', 'EUR', 'LIBRA'],
          cantidad:0,
          tengo:'USD',
          quiero:'EUR',
          total: 0
        }
    },
      methods:{
        convertirMoneda(){
          console.log('ejecutar metodo')
          switch(this.tengo) {
              case 'USD':
                if(this.quiero === 'USD'){
                      this.total = this.cantidad;
                }
                if(this.quiero === 'EUR'){
                      this.total = this.cantidad * 0.92;
                }
                if(this.quiero === 'LIBRA'){
                      this.total = this.cantidad * 0.77;
                }
                break;
              case 'EUR':
                if(this.quiero === 'USD'){
                        this.total = this.cantidad * 1.09;
                  }
                  if(this.quiero === 'EUR'){
                        this.total = this.cantidad;
                  }
                  if(this.quiero === 'LIBRA'){
                        this.total = this.cantidad * 0.84;
                  }
                  break;
                case 'LIBRA':
                  if(this.quiero === 'USD'){
                        this.total = this.cantidad * 1.29;
                  }
                  if(this.quiero === 'EUR'){
                        this.total = this.cantidad * 1.19;
                  }
                  if(this.quiero === 'LIBRA'){
                        this.total = this.cantidad;
                  }
                break;
              
          } 
        },
       /*getTotal(valor){
          return Math.round(valor)
        }*/

      }
  }
  </script>
  
  <style scoped>
  label{
    font-weight: 700;
    font-size: 120%;
    color: white;
  }
  .badge{
    margin: 2px;
    font-size: 150%;
    color:cornsilk;

  }
  </style>
  