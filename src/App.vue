<template>
  <v-app>
    <v-card
    width="80%"
    class="mx-auto my-4"
  >
    <v-card-title>
      <p class="my-auto" style="padding-left: 28px;">Lista linków</p>
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
      list: true,
      links:[]
    }
    //
  },
  created: function(){
    console.log('test');
    
    fetch("/api/login", {
        method: "post",
        headers: {
            "Content-type": "application/json; charset=UTF-8"
        },
        body: JSON.stringify({email:'admin',password:'admin'})
    }).then(res => {
      return res.text()
    })
    .then(res => {
        console.log(res);
    })

    fetch("/api/links").then(res => res.json()).then(res =>{
      console.log(res)
      this.links = res;
    })
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
