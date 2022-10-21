<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

     
    </v-row>
    <v-row class="text-center">
      <v-card
    
      class="mx-auto my-12"
      max-width="374"
    >
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>
  
      <v-img
        height="250"
        src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
      ></v-img>
  
      <v-card-title style="text-align: center;" >login</v-card-title>
  
  
      <v-divider class="mx-4"></v-divider>
  
      <v-card-title>Tonight's availability</v-card-title>
  
      <v-card-text>
        <div class="form">
          <input type="email" name="email" id="email" placeholder="Email" v-model.trim="email">
          <input type="password" name="password" id="password" placeholder="Password" v-model="password">
          <p class="erorrs" :class="{ empty_fild:email_error}">Please write your EMAIL</p>
          <p class="erorrs" :class="{ empty_fild:password_error}">Please write password</p>
        </div>
      </v-card-text>
      <v-card-actions>
        <v-btn
          color="deep-purple lighten-2"
          text
          @click="login()"
        >
        Login
        </v-btn>
      </v-card-actions>
    </v-card>

    </v-row>
  </v-container>

</template>

<style scoped>
.form{
  display: flex;
  flex-direction: column;
}
.form>input {
  border: 2px solid grey;
padding-left: 5px;
}

.erorrs{
  list-style: none;
  color:red;
  font-style: italic;
  font-weight: 400;
  font-size: 0.8rem;
  line-height: 1rem;
  border-radius:0.313rem;
  display: none;
  width: 100%;
  margin-bottom:0.313rem;
}
.empty_fild{
  display: block;
}
#email{

}
#password{

}

</style>

<script>
import { required, minLength, between, email } from 'vuelidate/lib/validators'
import { useVuelidate } from 'vuelidate/lib/validators'
import { reactive } from 'vue' 
import Vuelidate from 'vuelidate'

import json from '../../products/products.json'
// console.log(json);

  export default {
    name: 'HelloWorld',

    data: () => ({
      products : json.products,
      email: '',
      password: '',
      email_error: false,
      password_error: false,
    }),
 
    methods:{
      login: function(){
       
        this.email_error = false;
        this.password_error = false;
        let flag = true;

        if (!this.email || !this.validEmail(this.email)) {
          this.email_error = true;
          flag = false;
         // return;
        }
        if (!this.password || this.password.length <= 6) {
          this.password_error = true;
          flag = false;
        //  return;
        } 
        console.log(this.email_error );
        console.log(this.password_error);
        if(!flag){
          return;
        }
        
        this.$router.push('Products')

        },
        validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    },
  }
</script>
