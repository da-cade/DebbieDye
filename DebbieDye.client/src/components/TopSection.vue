<template>
  <div class="parallax bg">
    <div class="word-wrapper text-info">
      <h1>Debbie Dye</h1>
      <h2 class="fw-bold">Real Estate Transaction Coordinating Services</h2>
      <span class="d-flex"
        ><div class="mdi mdi-format-quote-open"></div>
        <h5>Be a ray of sunshine in someones life to make it a brighter day</h5>
        <div class="mdi mdi-format-quote-close pt-1"></div
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.parallax {
  position: relative;
  transform-style: preserve-3d;
  z-index: 2;
  @media (min-width: 1400px) {
    min-height: 93vh;
  }
  @media (max-width: 1400px) {
    min-height: 95vh;
  }
  @media (max-width: 1200px) {
    min-height: 95vh;
  }
  @media (max-width: 992px) {
    min-height: 95vh;
  }
  @media (max-width: 768px) {
    min-height: 95vh;
  }
  @media (max-width: 578px) {
    min-height: 95vh;
  }
  @media (max-height: 500px) and (orientation: landscape) {
    min-height: 100vh;
  }
}

.bg::after {
  transform: translateZ(-1px) scale(1.8);
}

.word-wrapper {
  position: absolute;
  z-index: 2;
  color: white;
  padding: 2em;
  width: 70vw;
  top: 30%;
  left: 10%;

  @media (max-width: 576px) {
    top: 10%;
    left: 0;
    width: auto;
  }
}
</style>
