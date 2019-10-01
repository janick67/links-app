<template>
  <v-container>
    <v-layout row>
      <v-flex xs12 sm6 offset-sm3>
        <v-card>
          <v-card-text>
            <v-container>
              <form @submit.prevent="onSignin">
                <v-layout row>
                  <v-flex xs12>
                    <v-text-field
                      name="username"
                      label="Username"
                      v-model="username"
                      required></v-text-field>
                  </v-flex>
                </v-layout>
                <v-layout row>
                  <v-flex xs12>
                    <v-text-field
                      name="password"
                      label="Password"
                      id="password"
                      v-model="password"
                      type="password"
                      required></v-text-field>
                  </v-flex>
                </v-layout>
                <v-layout row>
                  <v-flex xs12>
                    <v-btn type="submit">
                      Sign in
                       <span slot="loader" class="custom-loader">
                        <v-icon light>mdi-cached</v-icon>
                       </span>
                    </v-btn>
                  </v-flex>
                </v-layout>
              </form>
            </v-container>
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    onSignin () {
       console.log('loguje się...')
      fetch("/api/login", {
          method: "post",
          headers: {
              "Content-type": "application/json; charset=UTF-8"
          },
          body: JSON.stringify({username: this.username ,password: this.password})
      }).then(res => {
        return res.json()
      })
      .then(res => {
          console.log(res);
          if (res.user !== null) {
            this.$emit('Signed')
            } 
          if (res.error !== null) console.log(res.error)
      })
    }
  }
}
</script>
