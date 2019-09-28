<template>
  <v-app>
    <v-card
    width="100%"
    class="mx-auto"
  >
    <v-card-title>
      Lista linków
      <div class="flex-grow-1"></div>
      <v-btn icon v-on:click="chooseList">
        <v-icon>mdi-format-list-bulleted</v-icon>
      </v-btn>
      <v-btn icon v-on:click="chooseGrid">
        <v-icon>mdi-grid</v-icon>
      </v-btn>
    </v-card-title>
    <v-card-text>
      <v-container v-if="list">
        <v-list>
          <v-list-item-group>
            <ListElem :link="link"  v-for="link in links" :key="link.id"/>
          </v-list-item-group>
        </v-list>
      </v-container>
      <v-container v-else class="d-flex align-content-start flex-wrap">
        <myCard :link="link" v-for="link in links" :key="link.id" />
      </v-container>
    </v-card-text>
  </v-card>
  </v-app>
</template>

<script>
import myCard from './components/myCard.vue';
import ListElem from './components/ListElem.vue';

export default {
  name: 'App',
  components: {
    myCard,
    ListElem
  },
  data: function () {
    return{
      list: false,
      links:[
        {
          id:1,
          name:'Google',
          url: 'https://www.google.com/',
          description:'wyszukiwarka'
        },
        {
          id:2,
          name:'Gmail',
          url:'https://www.google.com/gmail',
          description:'poczta'
        },
        {
          id:3,
          name:'YouTube',
          url:'https://www.youtube.com',
          description:'rozrywka'
        },
        {
          id:4,
          name:'Facebook',
          url:'https://www.facebook.com/',
          description:'media społecznościowe'
        },
        {
          id:1+4,
          name:'Google',
          url: 'https://www.google.com/',
          description:'wyszukiwarka'
        },
        {
          id:2+4,
          name:'Gmail',
          url:'https://www.google.com/gmail',
          description:'poczta'
        },
        {
          id:3+4,
          name:'YouTube',
          url:'https://www.youtube.com',
          description:'rozrywka'
        },
        {
          id:4+4,
          name:'Facebook',
          url:'https://www.facebook.com/',
          description:'media społecznościowe'
        },
             {
          id:1+8,
          name:'Google',
          url: 'https://www.google.com/',
          description:'wyszukiwarka'
        },
        {
          id:2+8,
          name:'Gmail',
          url:'https://www.google.com/gmail',
          description:'poczta'
        },
        {
          id:3+8,
          name:'YouTube',
          url:'https://www.youtube.com',
          description:'rozrywka'
        },
        {
          id:4+8,
          name:'Facebook',
          url:'https://www.facebook.com/',
          description:'media społecznościowe'
        }
      ]
    }
    //
  },
  methods:{
    chooseList: function(){
      this.list = true;
    },
    chooseGrid: function(){
      this.list = false;
    }
  }
};
</script>
