<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input v-model="searchValue" @input="handleInput" id="search" name="search">
      <ul>
        <li v-for="result in results" :key="result.data[0].nasa_id">
          <p>{{ result.data[0].description }} </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios';
import debounce from "lodash.debounce";

Vue.use(VueAxios, axios);
const API = "https://images-api.nasa.gov/search";
export default {
  name: "Search",
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    /* exlin-disable */
    handleInput: debounce(function() {
      {
        axios.get(`${API}?q=${this.searchValue}&media_type=image`)
          .then(response => {
            this.results = response.data.collection.items;
          })
          .catch(error => {
            console.log(error);
          });
      }
    }, 500)
  }
};
</script>
<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
}
.search {
  display: flex;
  flex-direction: column;
  width: 300px;
}

label {
  font-size: 25px;
  text-align: center;
  font-family: Montserrat, sans-serif;
}

input {
  height: 30px;
  border: none;
  border-bottom: 1px solid black;
  outline: none;
}
</style>

