<template>
  <main>
    <Navbar @scroll="scrollToElement" />
    <div ref="Landing"></div>
    <TopSection />
    <div ref="Bio"></div>
    <BioSection />
    <div ref="Services"></div>
    <ServicesSection />
    <div ref="Reviews"></div>
    <ReviewsSwiper />
    <Footer />
  </main>
</template>

<script>
export default {
  name: "Home",
  methods: {
    scrollToElement(target) {
      console.log(target);
      let el = this.$refs[target];
      if (el) {
        el.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
};
</script>

<style scoped lang="scss">
@import "src/public/assets/scss/_variables.scss";
</style>
