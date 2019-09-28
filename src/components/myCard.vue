<template>
  <v-card
    width="250"
    class="mx-auto mt-5"
  >
    <v-card-title>{{link.name}}</v-card-title>
    <v-card-text>{{link.url}}</v-card-text>
  </v-card>
</template>

<script>
export default {
  props:['link'],
  data: () => ({
   
  }),
};
</script>
