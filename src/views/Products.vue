<template>
    <v-container>
   
  
      <v-row class="text-center">
  
        <v-col
          class="mb-5"
          cols="12"
        >
          <v-row justify="center">
            <a
              v-for="(eco, i) in products"
              :key="i"
              :href="'#/product/'+eco.id"
              class="subheading mx-3"
              target="_blank"
              style="border: 2px solid grey;margin-top:10px; border-radius: 5px;"
            >
            <h2>{{ eco.title }}</h2>
            <v-img
              :src="eco.images[0]"
              class="my-3"
              contain
              height="100"
            />
            $ {{eco.price}}
            </a>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  
  </template>
  
  <style scoped>

  
  </style>
  
  <script>
  
  import json from '../../products/products.json'
  // console.log(json);
  
    export default {
      name: 'Products',
  
      data: () => ({
        products : json.products,
  
      }),
      mounted() {
      // console.log(this.products);
    },
    }
  </script>
  