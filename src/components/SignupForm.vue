
<template>    
        <form id="signup-form" v-on:submit.prevent="submit">
            <div class="row">
                <div class="col-12 form-group">
                    <label class="col-form-label col-form-label-lg">Vehicle name<span class="text-danger">*</span></label>       
                    <input type="text" v-model.trim="$v.name.$model" :class="{'is-invalid': true}" v-model="message" class="form-control form-control-lg"> 
                    <div v-if="!$v.name.required" class="invalid-feedback">
                    The name field is required
                    </div>
                </div>
                <div class="col-12 form-group">
                    <label class="col-form-label col-form-label-lg">Vehicle type<span class="text-danger">*</span></label>       
                    <select  v-model="selected"  class="form-control form-control-lg">
                        <option disabled >Select type</option>
                        <option v-for="item in items" :key="item.vehicleType">{{item.vehicleType}}</option>
                    </select> 
                    
                </div>
                <div class="col-12 form-group">
                    
                    <b-button v-b-modal.my-modal>Submit</b-button>
                      <!-- The modal -->
                      <b-modal id="my-modal">
                          <p>The vehicle name is {{message}} </p>
                          <p>The vehicle type  is {{selected}} </p>
                      </b-modal>
                    
                </div>
            </div>
           
            
            
        </form>  
        
      
</template>

<script>
import { required } from 'vuelidate/lib/validators'
import vehicles from '../vehicles.json'

    export default {
    name:'SignupForm',
    data: function(){
      return {
        items: vehicles,
        name: '',
        type: '',
        selected: ''
      }
    },
    validations: {
      name: {required}
    },

    methods: {
      submit: function(){
        this.$v.$touch();
        if (this.$v.$pendding || this.$v.$error) return;
      }
    
    }
    
    }


</script>