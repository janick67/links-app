<template>
  <v-card
    width="250"
    class="mx-auto mt-5"
    @click="onClick"
  >
  <v-img
      :src="link.imageURL"
      width="250"
      height="150"
    ></v-img>
    <v-card-title>{{link.name}}</v-card-title>
    <v-card-text>{{link.url}}</v-card-text>
  </v-card>
</template>

<script>
export default {
  props:['link'],
  methods:{
    onClick: function(){
      window.open(this.link.url, '_blank')
    }
  }
};
</script>
