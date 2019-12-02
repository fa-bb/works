<template>
  <v-expansion-panels>
    <v-expansion-panel
      v-for="item in arr"
      :key="item.id"
    >
    <v-expansion-panel-header>{{item.title}}</v-expansion-panel-header>
      <v-expansion-panel-content>
        like数    :{{item.likes_count}}<br>
        コメント数:{{item.comments_count}}<br>
        URL       :<a :href="item.url">{{item.title}}</a>
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
