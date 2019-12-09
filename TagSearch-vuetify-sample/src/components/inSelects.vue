<template>

  <v-container>
    <v-combobox
      v-model="chipsdata"
      :items="suggestdata"
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
        </v-chip>
      </template>
    </v-combobox>
  
    <panels :arr="itemsdata" />

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
    data () {
      return {
        chipsdata: this.chips,
        itemsdata: this.items,
        suggestdata: this.suggest
      }
    },
    methods: {
      remove (item) {
        this.chipsdata.splice(this.chipsdata.indexOf(item), 1)
        this.chipsdata = [...this.chipsdata]
      },

      getAnswer: function(){

        console.log(this.chipsdata)

        var keyword = this.chipsdata.join(" ");
        console.log(keyword)

        var vm = this

        var params = { page: 1, per_page:20, query: keyword}
        axios.get('https://qiita.com/api/v2/items',{params})
          .then(function(response){
            console.log(response)
            vm.itemsdata = response.data
            console.log("form this.items"+vm.itemsdata)
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
