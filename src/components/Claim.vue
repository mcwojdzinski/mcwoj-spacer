<template>
  <div class="ClaimWrapper">
    <h1 class="claim">SPACER</h1>
    <p
      class="subclaim"
    >Begin your journey through our amazing galaxy, and discover places you never even heard of.</p>
    <p class="subclaim">Type anything space-related to start.</p>
  </div>
</template>
<script>
export default {
  name: "Claim"
};
</script>


<style lang="scss">
.ClaimWrapper {
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.claim {
  font-size: 50px;
  margin: 0;

  @media (min-width: 768px) {
    font-size: 80px;
  }

  @media (min-width: 1024px) {
    font-size: 100px;
  }
}

.subclaim {
  font-size: 13px;
  margin: 20px 0 0 0;

  @media (min-width: 768px) {
    font-size: 18px;
    letter-spacing: 1px;
    width: 500px;
  }
}
</style>
