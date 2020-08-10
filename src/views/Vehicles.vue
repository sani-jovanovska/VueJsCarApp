
<template>
  <div id="vehicles">
    <h1>{{header}}</h1>
    <div class="row">
        <div class="column"> 
        <h3>Vehicle name</h3>
        </div>
        <div class="column"> 
        <h3>Vehicle type</h3>
        </div>
        <div class="column"> 
        <h3>Model</h3>
        </div>
        <div class="column"> 
        <h3>Plate number</h3>
        </div>

    </div>
    
    <div class="row" v-for="item in items" :key="item.vehicleName">   
      
        <div class="column">       
        {{item.vehicleName}}
        </div>
        <div class="column">
        {{item.vehicleType}}
        </div>
        <div class="column">
        {{item.model}}
        </div>
        <div class="column">
        {{item.plateNumber}}
        </div>    
        <div class="column">       
          <button >EDIT</button>
          <button @click="deleteFromList(this.item)">DELETE</button>
        </div> 
		
    </div>
  </div>
</template>

<script>
import vehicles from '../vehicles.json'
export default {

  data() {
    return{
      items: vehicles,
      header: "This is a vehicle page"      
    }
  },
  methods: {
    deleteFromList(index) {
      this.list.splice(index, 1);
    }

  },

  created () {
    console.log(vehicles);
  }

}


</script>

<style>
.row {
  display: flex;
}
.column {
  float: left;
  width: 15%;  
  padding: 10px;
}

</style>