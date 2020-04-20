<template>
  <v-card raised min-height="360px" class="d-flex flex-column">
    <v-card-title>Step: {{counter.step}}</v-card-title>
    <v-divider></v-divider>
    <div class="d-flex text-center justify-center counter-number align-center">
        {{counter.value}}
        </div>
    <v-btn @click="runCounter" height="50px" color="light-blue" class="mx-auto" dark width="70%">Run</v-btn>
  </v-card>
</template>


<script>
// get counter object with counter prop from parent component
export default {
  props: {
    counter: {
      type: Object
    }
  },
  methods:{
    // calculate counter new value 
      runCounter(){
        let newValue=this.counter.value+this.counter.step
        if(Number.isInteger(newValue)){
          this.counter.value=newValue
        } else{
          this.counter.value=parseFloat(newValue.toFixed(1))
        }
      }
  }
}
</script>

<style scoped>
.counter-number{
    font-size: 5em;
    min-height: 230px;
}
</style>