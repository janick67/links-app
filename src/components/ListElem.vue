<template>
<v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title><a :href="link.url" target="_blank">{{link.name}}</a></v-list-item-title>
        <v-list-item-subtitle>{{link.description}}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
</template>

<script>
export default {
  props:['link'],
  data: () => ({
   
  }),
};
</script>
