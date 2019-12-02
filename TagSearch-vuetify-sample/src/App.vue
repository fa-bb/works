<template>
  <v-app>
    <inSelects :chips="chips" :items='testData' :suggest='suggestions'/>
  </v-app>

</template>

<script>
import inSelects from './components/inSelects';

export default {
  name: 'App',

  components: {
    inSelects,
  },

  data:function(){
    return{
        // chips: ['Programming', 'Playing video games', 'Watching movies', 'Sleeping'],
        // testData:['red','green','blue']
        chips: [],
        testData:[],
        suggestions:["Java","JavaScript","ruby","swift","rails","PHP","Android","Dart","vim"]
    }
  }

};

</script>
