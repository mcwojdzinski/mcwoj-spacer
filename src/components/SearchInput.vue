<template>
  <div class="searchWrapper">
    <input v-model="searchValue" @input="handleInput" id="search" name="search">
  </div>
</template>
<script>
export default {
  name: "SearchInput"
};
</script>

<style lang="scss">
.searchWrapper {
  margin-top: 50px;
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
  border-bottom: 1px solid white;
  outline: none;
  background: none;
  color: white;
}

input:focus {
  color: white;
}
</style>
