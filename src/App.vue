<template>
  <div class="wrapper">
    <BackgroundImage/>
    <Claim/>
    <SearchInput v-model="searchValue" @input="handleInput"/>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
import debounce from "lodash.debounce";
import Claim from "@/components/Claim";
import SearchInput from "@/components/SearchInput";
import BackgroundImage from "@/components/BackgroundImage";

Vue.use(VueAxios, axios);
const API = "https://images-api.nasa.gov/search";
export default {
  name: "App",
  data() {
    return {
      searchValue: "",
      results: []
    };
  },
  components: {
    Claim,
    SearchInput,
    BackgroundImage
  },
  methods: {
    /* exlin-disable */
    handleInput: debounce(function() {
      console.log(this.searchValue);
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then(response => {
          this.results = response.data.collection.items;
        })
        .catch(error => {
          console.log(error);
        });
    }, 500)
  }
};
</script>


<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,600,800&subset=latin-ext");

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: "Montserrat", sans-serif;
  margin: 0;
  padding: 0;
  color: white;
}

.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  min-height: 100vh;
}
</style>
