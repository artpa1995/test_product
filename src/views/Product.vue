<template>
    <v-container>
      <v-row class="text-center">
        <v-col
          class="mb-5"
          cols="12"
        >
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
  
      <v-carousel>
      <v-carousel-item
        v-for="(item,i) in this.singleProduct.images"
        :key="i"
        :src="item"
        reverse-transition="fade-transition"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
  
      <v-card-title>{{this.singleProduct.title}}</v-card-title>
      <v-card-title>Category: {{this.singleProduct.category}}</v-card-title>
      <v-card-title>Brand: {{this.singleProduct.brand}}</v-card-title>
  
      <v-card-text>
        <v-row
          align="center"
          class="mx-0"
        >
          <v-rating
            :value="4.5"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>
  
          <div class="grey--text ms-4">
            {{this.singleProduct.discountPercentage}}
            
          </div>
        </v-row>
  
        <div class="my-4 text-subtitle-1">
          $ {{this.singleProduct.price}}
        </div>
        
        <div>{{this.singleProduct.description}}</div>
      </v-card-text>
  
  
   
    </v-card>
        </v-col>
      </v-row>
    </v-container>
  
  </template>
  
  <style scoped>

  
  </style>
  
  <script>
  
  import json from '../../products/products.json'

        export default {
            name: 'ProductSingle',
        data() {
            return {
            products: json,
            singleProduct: undefined,

            }
        },
        computed: {
            productId () {
            return this.$route.params.id;
            }
        },
        created () {
            this.assignSingleProduct();
        },
        methods: {
            assignSingleProduct() {
            let data = this.products.products;
            let product = data.filter(item => {
                return item.id == this.productId;
            })
           
            this.singleProduct = product[0];
            }
        }
        }
    
  </script>
  