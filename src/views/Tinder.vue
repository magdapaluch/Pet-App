<template>
  <v-app>
    <v-content class="dogs-layout">
      <v-container fill-height>
        <div class="dogs-overlay">
          <h1 class="display-2 text-xs-center">Choose your favorite dogs</h1>
          <v-card class="dog-card">
            <v-img :src="this.image" height="400px"></v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn icon>
                <v-icon>favorite</v-icon>
              </v-btn>
              <v-btn icon>
                <v-icon @click="loadNewImage">forward</v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </div>
      </v-container>
    </v-content>
  </v-app>
</template>


<script>
import axios from "axios";
axios.defaults.baseURL = "https://dog.ceo/api";

export default {
  data() {
    return {
      image: ""
    };
  },

  methods: {
    loadNewImage() {
      axios
        .get("/breeds/image/random")
        .then(response => {
          this.image = response.data.message;
          console.log(this.image);
        })
        .catch();
    }
  },
  created() {
    this.loadNewImage();
  }
};
</script>
