<template>
  <v-expansion-panels>
    <v-expansion-panel
      v-for="item in arr"
      :key="item.id"
    >
    <v-expansion-panel-header>{{item}}</v-expansion-panel-header>
      <v-expansion-panel-content>
        color
      </v-expansion-panel-content>
    </v-expansion-panel>
  </v-expansion-panels>

</template>

<script>

export default {
  props:{
    arr:Array
  }
};
</script>
