<template>
  <div class="wrapper">
    <Claim/>
    <SearchInput/>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
import debounce from "lodash.debounce";
import Claim from "@/components/Claim";
import SearchInput from "@/components/SearchInput";

Vue.use(VueAxios, axios);
const API = "https://images-api.nasa.gov/search";
export default {
  name: "Search",
  data() {
    return {
      searchValue: "",
      results: []
    };
  },
  components: {
    Claim,
    SearchInput
  },
  methods: {
    /* exlin-disable */
    handleInput: debounce(function() {
      {
        axios
          .get(`${API}?q=${this.searchValue}&media_type=image`)
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
  justify-content: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  background-image: url("../assets/backgroundImage.jpg");
  background-repeat: no-repeat;
  background-position: bottom;
  background-size: cover;
  height: 100vh;
  width: 100%;
}
</style>
