<template>
  <v-combobox
    v-model="chips"
    :items="items"
    chips
    clearable
    label="Your favorite hobbies"
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
        <span>(interest)</span>
      </v-chip>
    </template>
  </v-combobox>
</template>

<script>
  export default {
    props:{
     chips:Array,
     items:Array
    },
    methods: {
      remove (item) {
        this.chips.splice(this.chips.indexOf(item), 1)
        this.chips = [...this.chips]
        this.$App.chips = this.chips 
      },
    },
  }
</script>
