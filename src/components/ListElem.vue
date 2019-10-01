<template>
<v-list-item two-line @click="onClick">
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
