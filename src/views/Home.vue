<template>
  <div class="home">
    <h1>Adopt a new best friend</h1>
    <button v-on:click="toggleForm" class="btn btn-primary">add a new pet</button>

    <template>
      <div>
        <b-form @submit.prevent="handleSubmit" v-if="petForm">
          <b-form-group id="input-group-2" label="Pet's Name:" label-for="input-2">
            <b-form-input
              id="input-2"
              type="text"
              v-model="formData.name"
              required
              placeholder="Enter name"
            ></b-form-input>
          </b-form-group>

          <b-form-group id="input-group-3" label="Species:" label-for="input-3">
            <b-form-select
              id="input-3"
              v-model="formData.species"
              :options="['cats', 'dogs']"
              required
            ></b-form-select>
          </b-form-group>

          <b-form-group id="input-group-2" label="Pet's Age:" label-for="input-2">
            <b-form-input
              id="input-2"
              type="number"
              v-model="formData.age"
              required
              placeholder="Enter age"
            ></b-form-input>
          </b-form-group>

          <b-button type="submit" variant="primary">Submit</b-button>
          <b-button type="reset" variant="danger">Reset</b-button>
        </b-form>

      </div>
    </template>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'Home',
  data () {
    return {
      petForm: false,
      formData: {
        name: '',
        age: 0,
        species: null
      }
    }
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    toggleForm () {
      this.petForm = !this.petForm
    },
    handleSubmit () {
      const { species, name, age } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload)

      this.formData = {
        name: '',
        age: 0,
        species: null
      }
    }
  }
}

</script>
