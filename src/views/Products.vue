<template>
  <div class="product">
    <h1>hola</h1>
    <v-row v-for="product in filterList" :key="product.id" cols="4">
      <v-col cols="6">
        <v-img :src="product.image_link"></v-img>
      </v-col>
      <v-col cols="6">     
        <v-card-title>{{product.name}}</v-card-title>     
        <v-card-text>{{product.description}}</v-card-text>
        <v-card-text>Precio: {{product.price}}</v-card-text>
        <v-btn color="success" @click="addCart(product)">Agregar al carro</v-btn>   
        <v-btn color="error" @click="deleteToCart(product)" v-model="boton" :disabled = "!disableButton"><v-icon>mdi-cart-off</v-icon>Quitar del carro</v-btn>      
        <h3></h3>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import { mapState, mapActions } from "vuex";
export default {
  data: () => ({
    boton: Boolean
  }),
  computed: {
    ...mapState(["products", "product", "cart"]),
    parametro() {
      return this.$route.params.id;
    },
    filterList() {
      return this.products.filter((product) => {
        return product.id == this.$route.params.id;
      });
    },   
  },
  methods: {
    ...mapActions(["setProducts", "addCart", "removeCart"]),
   deleteToCart(product){
     this.removeCart(product)
   },

   disableButton(){
     if(this.cart.length> 0){
       this.boton  = false
     }else{
       this.boton = true
     }
   }






/*
    deleteToCart(product){
      if(this.cart.length >= 0){
        this.removeCart(product)       
      },
       this.buttonRemove()
     
    },
     buttonRemove(){
       return this.cart.length >= 0 ? true : false
     }*/

  },
  created: function () {
    if (this.products.length == 0) {
      this.setProducts();
    }
  },
};
</script>