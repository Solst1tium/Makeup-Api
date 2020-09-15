<template>
  <div class="home">
    <v-container>
      <v-text-field v-model="search" append-icon="mdi-magnify" label="Busca un producto" single-line hide-details></v-text-field>
      </v-container>
    <v-row>      
    <v-col v-for="product in filterList" :key="product.id" cols="4">
    <v-card class="mx-auto">     
      <v-img :src="product.image_link" height="200px"></v-img>
      <v-card-title>
      {{ product.name }}
      </v-card-title>        
      <v-card-subtitle> Precio: {{product.price}} </v-card-subtitle>
      <v-card-actions>        
       <v-btn color="warning" :to="'/products/'+product.id">Ver más</v-btn>
        <v-spacer></v-spacer>       
      </v-card-actions>     
    </v-card>  
    </v-col>
  </v-row>
  </div>
</template>

<script>
import {mapState, mapActions } from 'vuex'

export default {
   data: () => ({
     show: false,
      search: ''
    }),
  name: 'Home',
  components: { 
   
  },
  methods: {
    ...mapActions(['setProducts'])
  },
  computed:{
    ...mapState(['products']),
    filterList(){
      return this.products.filter((product) => {
        return product.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  },
  created: function () {
    this.setProducts();
  }
}
</script>
