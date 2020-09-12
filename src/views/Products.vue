<template>
  <v-content>
    <v-row>
      <v-col cols="6">
        <v-img :src="product.image_link" height="200px"></v-img>
      </v-col>
    </v-row>
 
     <v-row>
      <v-col cols="6">
        <v-card-title>{{product.name}}</v-card-title>
      </v-col>
    </v-row>
  </v-content>
</template>
<script>

export default {

  
}
</script>