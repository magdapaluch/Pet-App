<template>
  <div>
    <v-form>
      <v-text-field label="Breed" v-model="breed"></v-text-field>
      <v-btn @click="submit">Submit</v-btn>
    </v-form>
    <v-container grid-list-md fluid>
      <v-layout wrap>
        <v-flex xs12 sm4 md3 v-for="dog in dogsImages" :key="dog">
          <v-img :src="dog" height="170px"></v-img>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";
axios.defaults.baseURL = "https://dog.ceo/api";

export default {
  data() {
    return {
      breed: "",
      dogsImages: []
    };
  },
  methods: {
    submit() {
      axios
        .get("/breed/" + this.breed + "/images")
        .then(response => {
          this.dogsImages = response.data.message.slice(0, 8);
        })
        .catch(console.log("error"));
    }
  }
};
</script>
