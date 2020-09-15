<template>
<v-app>
  <v-container grid-list-xs>
    <v-app-bar app color="dark" dark>
      <v-toolbar-title></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/" text>home</v-btn>
      <v-btn to="/products" text>Productos</v-btn>
      <v-spacer></v-spacer>
        <v-btn color="success"> <v-icon>mdi-cart</v-icon>carro: {{carro}}</v-btn>   
     <h1> </h1>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>    
    <v-footer
        absolute
        class="font-weight-medium" color="indigo lighten-4">
        <v-col class="text-center" cols="12">
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
        </v-col>
      </v-footer>
   </v-container>
  </v-app>  
</template> 

<script>
import { mapState} from "vuex";
export default {
  name:"app",

 computed: {
   ...mapState(["cart"]),
    carro() {
      return this.cart.length;
    },
 },
}
</script>
