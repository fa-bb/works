<template>
  <v-app>
    <v-content>
      <inSelects v-bind:chips="chips" />
      <panels v-bind:child-firld.sync="firldComputed"/>
    </v-content>
  </v-app>


</template>

<script>
import inSelects from './inSelects';
import panels from './panels';

export default {
  name: 'TagSearch',
};
</script>
