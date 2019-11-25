<template>

  <div>
    <Header :username='name'></Header>  
  </div>

</template>

<script>
import Header from './components/Header.vue'

export default {
  components: {
    Header
  },
  data(){
    return{
      name:"props only test"
    }
  }
}
</script>

