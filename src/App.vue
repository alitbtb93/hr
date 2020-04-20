<template>
  <v-app>
    <v-container>
     <counterForm @counters="addCounters"/>
     <v-row>
       <v-col class="my-5" v-for="(counter,index) in counters" :key="index" cols="12" md="3">
         <counterBox :counter="counter"/>
       </v-col>
     </v-row>
    </v-container>
  </v-app>
</template>

<script>
import counterForm from './components/counterForm'
import counterBox from './components/counterBox'
export default {
  name: "App",
  data(){
    return{
      counters:null
    }
  },
  components: {
    counterForm,
    counterBox
  },
  methods:{
    addCounters(value){
      this.counters=value
    }
  }

  
};
</script>
