<template>

  <v-container>
    <v-combobox
      v-model="chips"
      :items="suggest"
      chips
      clearable
      @input="getAnswer"
      label="input Your Search keywords"
      multiple
      prepend-icon=""
      solo
      >
      <template v-slot:selection="{ attrs, item, select, selected }">
        <v-chip
      v-bind="attrs"
      :input-value="selected"
      close
      @click="select"
      @click:close="remove(item)"
      >
      <strong>{{ item }}</strong>&nbsp;
      <!-- <span>(interest)</span> -->
        </v-chip>
      </template>
    </v-combobox>
  
    <panels :arr="items" />

  </v-container>

</template>

<script>
import panels from './panels';
import axios from 'axios';

  export default {
    components:{
      panels
    },
    props:{
     chips:Array,
     items:Array,
     suggest:Array
    },
    methods: {
      remove (item) {
        this.chips.splice(this.chips.indexOf(item), 1)
        this.chips = [...this.chips]
      },
      getAnswer: function(){

        var keyword = this.chips.join(" ");
        console.log(keyword)

        var vm = this

        var params = { page: 1, per_page:20, query: keyword}
        axios.get('https://qiita.com/api/v2/items',{params})
          .then(function(response){
            console.log(response)
            vm.items = response.data
            console.log("form this.items"+vm.items)
          })
          .catch(function(error){
            console.log(error)
          })
          .finally(function(){
            console.log('Search finish')
          })

      }
    }
  }

</script>
