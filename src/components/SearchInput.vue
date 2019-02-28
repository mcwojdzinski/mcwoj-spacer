<template>
  <input :value="value"
    id="search"
    name="search"
    @input="handleChange">
</template>
<script>
export default {
  name: "SearchInput",
  props: {
    value: {
      type: String,
      required: true
    }
  },
  methods: {
    handleChange(e) {
      this.$emit("input", e.target.value);
    }
  }
};
</script>

<style lang="scss">
input {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  width: 300px;
  text-align: center;
  font-size: 18px;
  font-weight: 600;
  height: 30px;
  border: none;
  border-bottom: 1px solid white;
  outline: none;
  background: none;
  color: white;
  transition: box-shadow 0.5s;

  @media (min-width: 1024px) {
    font-weight: 400;
  }
}

input:focus {
  color: white;
  box-shadow: 0 10px 20px -8px rgba(255, 255, 255, 0.3);
}
</style>
