<template>
  <v-app>
    <v-container>
      <!-- listen to counterForm component for new counter -->
     <counterForm @counters="addCounters"/>
     <v-row>
       <v-col class="my-5" v-for="(counter,index) in counters" :key="index" cols="12" sm="6" md="3">
         <!-- pass counter object to counterBox component with prop -->
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
    // add new counter object to counters array
    addCounters(value){
      this.counters=value
    }
  }

  
};
</script>
