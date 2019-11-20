<template>
  <v-app>
    <v-content>
      <inSelects/>
      <panels/>
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

  data: () => ({
    //
  }),
};
</script>
