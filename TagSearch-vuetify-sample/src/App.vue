<template>
  <v-app>
    <inSelects :chips="chips" :items='testData' :suggest='suggestions'/>
  </v-app>

</template>

<script>
import inSelects from './components/inSelects';
import axios from 'axios';

export default {
  name: 'App',

  components: {
    inSelects,
  },

  data:function(){
    return{
        chips: [],
        testData:[],
        suggestions:[]
    }
  },
  created: function(){
    var vm = this
    console.log('start created')
    var params = { page: 1, per_page:30, sort: "count"}
    axios.get('https://qiita.com/api/v2/tags',{params})
      .then(function(response){

        for(let i of response.data) {
          vm.suggestions.push(i.id)
        }
        console.log(vm.suggestions)

      })
      .catch(function(error){
        console.log(error)
      })
      .finally(function(){
        console.log('conputed finish')
      })

  }

};

</script>
