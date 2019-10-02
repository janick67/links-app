<template>
<v-list-item two-line @click="onClick">
  <v-list-item-avatar>
      <v-img
      :src="link.imageURL"
      weight="30"
      height="30"
    ></v-img>
        </v-list-item-avatar>
      <v-list-item-content>
        <v-list-item-title>{{link.name}}</v-list-item-title>
        <v-list-item-subtitle>{{link.description}}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
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
