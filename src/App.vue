<template>
  <v-app>
    <signin v-if="login_page" @Signed="onSigned"/>
    <v-card 
    v-else
    width="80%"
    class="mx-auto my-4"
  >
    <v-card-title>
      <div class="flex-grow-0">
        <v-img
        :src="logoURL"
        width="100"
        height="70"
        ></v-img>
      </div>
      <p class="my-auto" style="padding-left: 28px;">{{title}}</p>
      <div class="flex-grow-1"></div>
      <v-btn icon v-on:click="chooseList">
        <v-icon>mdi-format-list-bulleted</v-icon>
      </v-btn>
      <v-btn icon v-on:click="chooseGrid">
        <v-icon>mdi-grid</v-icon>
      </v-btn>
      <v-btn v-on:click="chooseList" class="ml-5" @click="onLogout">
        {{logoutText}} 
        <v-icon class="ml-1">mdi-exit-to-app</v-icon>
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
import Signin from './components/Signin.vue';

export default {
  name: 'App',
  components: {
    Signin,
    myCard,
    ListElem
  },
  data: function () {
    return{
      list: true,
      login_page: false,
      links:[],
      logoURL: 'https://dynamic.brandcrowd.com/asset/logo/4c8f8b36-51b9-4ebf-b20c-00e5c25719c3/logo?v=4&text=Logo+Text+Here',
      title: 'Lista linków',
      logoutText: 'Wyloguj'
    }
    //
  },
  created: function(){
     this.fetchData()
  },
  methods:{
    chooseList: function(){
      this.list = true;
    },
    chooseGrid: function(){
      this.list = false
    },
    onSigned: function(){
      this.login_page = false
      this.fetchData()
    },
    onLogout: function(){
      this.login_page = true
      this.links = [] 
      fetch(document.location.origin+"/api/logout").then(res=>this.fetchData())
    },
    fetchData: function(){
       console.log('pobieram dane...')

      fetch("/api/links").then(res => res.json()).then(res =>{
        console.log(res)
        if (res.error == 'Najpierw się zaloguj'){
          this.login_page = true;
        }else{
          this.links = res;
        }
      })
    }
  }
};
</script>
