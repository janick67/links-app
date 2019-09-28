<template>
  <v-app>
    {{links}}
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data: function () {
    return{
      links:[
        {
          name:'google',
          url: 'https://www.google.com/',
          description:'wyszukiwarka'
        },
        {
          name:'gmail',
          url:'https://www.google.com/gmail',
          description:'poczta'
        },
        {
          name:'YouTube',
          url:'https://www.youtube.com',
          description:'rozrywka'
        },
        {
          name:'YouTube',
          url:'https://www.facebook.com/',
          description:'media społecznościowe'
        }
      ]
    }
    //
  },
};
</script>
