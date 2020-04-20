<template>
  <v-card min-height="400px" class="d-flex flex-column">
    <v-card-title>Step: {{counter.step}}</v-card-title>
    <v-divider></v-divider>
    <div class="d-flex text-center justify-center font-weight-medium counter-number align-center">
        {{counter.value.toFixed(1)}}
        </div>
    <v-btn @click="runCounter" height="50px" color="light-blue" class="mx-auto" dark width="70%">Run</v-btn>
  </v-card>
</template>


<script>
export default {
  props: {
    counter: {
      type: Object
    }
  },
  methods:{
      runCounter(){
          this.counter.value+=this.counter.step
      }
  }
}
</script>

<style scoped>
.counter-number{
    font-size: 6em;
    min-height: 260px;
}
</style>