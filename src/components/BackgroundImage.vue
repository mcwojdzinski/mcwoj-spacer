<template>
  <div class="BackgroundImageWrapper"/>
</template>
<script>
export default {
  name: "BackgroundImage"
};
</script>
<style lang="scss" scoped>
.BackgroundImageWrapper {
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  z-index: -1;
  background-image: url("../assets/backgroundImage.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

.BackgroundImageWrapper::after {
  content: "";
  background: rgba(0, 0, 0, 0.5);
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  width: 100%;
  height: 100vh;
}
</style>
