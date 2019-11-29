<template>
  <v-app>
    <inSelects :chips="chips" :items='testData'/>
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
        chips: ['Programming', 'Playing video games', 'Watching movies', 'Sleeping'],
        testData:['red','green','blue']
    }
  }

};

</script>
