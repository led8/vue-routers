<template>
  <div>
    <h1>{{ animal.name }} ({{ $route.params.species }})</h1>
    <p>breed: {{ animal.breed }}</p>
    <p>gender: {{ animal.gender }}</p>
    <p>age: {{ animal.age }}</p>
    <p>color: {{ animal.color }}</p>
    <p>weight: {{ animal.weight }}</p>
    <p>at: {{ animal.location }}</p>
    notes: <h6>{{ animal.notes }}</h6>
  </div>
</template>

<script>
// import { mapState } from 'vuex'

export default {
  data () {
    return {
      animal: {}
    }
  },
  computed: {
    cats () {
      return this.$store.state.cats
    },
    dogs () {
      return this.$store.state.dogs
    }
    // ...mapState([
    //   'cats',
    //   'dogs'
    // ])
  },
  mounted () {
    const animal = this[this.$route.params.species][this.$route.params.id] // this.cats or this.dogs
    this.animal = animal
  }
}
</script>
