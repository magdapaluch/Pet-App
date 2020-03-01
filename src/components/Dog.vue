<template>
  <v-card color="grey lighten-2">
    <v-img v-if="dog.img" :src="dog.img" height="170px"></v-img>
    <v-card-title>
      <div>
        <h3>{{dog.name}}</h3>
        <p>{{dog.breed}}</p>
      </div>
    </v-card-title>
    <v-btn @click="$emit('addThisToFavorites', dog)">To Fav</v-btn>
    <v-btn to="/form">Adopt</v-btn>
  </v-card>
</template>
<script>
export default {
  props: {
    dog: {
      type: Object
    }
  }
};
</script>
<style></style>
