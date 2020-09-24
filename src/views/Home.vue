<template>
  <div class="home">  
    <h1>Adopt a new Best Friend.</h1>
    <button class="btn btn-primary" @click="togglePetForm">Add New Pet</button>
     
    <b-form v-if="showPetForm" @submit.prevent="handleSubmit"> 
      <b-form-group id="input-group-1" label="Pet's Name:" label-for="input-1" >
        <b-form-input
          id="input-1"
          v-model="formData.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>
       <b-form-group id="input-group-2" label="Pet's Age:" label-for="input-2">
        <b-form-input
          id="input-2"
          type="number"
          v-model="formData.age"
          required
          placeholder="Enter Age"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Pet's Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="formData.species"
          :options="['Cats','Dogs']"
          required
        ></b-form-select>
      </b-form-group>
 

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
// // @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  data() {
    return {
      showPetForm :false,
      formData: {
        name : '',
        age : '',
        species : null
      }
    }
  },
  methods : {
    ...mapActions ([
      'addPet' 
    ]),
    togglePetForm(){
      this.showPetForm = !this.showPetForm
    },
    handleSubmit(){
      const { species, age, name } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload),
      this.formData = {
        name : '',
        age : '',
        species : null
      }
      
    }
     
  } 
}
</script>
