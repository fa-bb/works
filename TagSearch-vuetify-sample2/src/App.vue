<template>
  <v-app>
    <v-content>
      <inSelects :chips="chips" :items='testData'/>
      <panels :arr="testData" />
    </v-content>
  </v-app>

</template>

<script>
import inSelects from './components/inSelects';
import panels from './components/panels';

export default {
  name: 'App',

  components: {
    inSelects,
    panels,
  },
  data:function(){
    return{
        chips: ['Programming', 'Playing video games', 'Watching movies', 'Sleeping'],
        testData:['red','green','blue']
    }
  },
  watch:{
    chips: function(){
      // console.log(value+" "+old)
    }
  }
  

};
</script>
