<template>
  <div class="no-parallax container-fluid bg-light">
    <div class="row d-flex justify-content-center">
      <h1 class="text-center mb-md-4">Reviews</h1>
      <div class="col-md-10 col-sm-12 swiper-container">
        <swiper
          :modules="modules"
          :pagination="true"
          :slides-per-view="1"
          @swiper="onSwiper"
          @slideChange="onSlideChange"
          class="mySwiper"
        >
          <swiper-slide
            ><div class="swiper-box">
              <p v-scrollanimation>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Consequatur nostrum dolorem eum inventore? Maiores molestiae
                nisi iure assumenda alias, facere architecto esse quasi
                similique? Magni molestiae repellat sunt pariatur et! Lorem
                ipsum dolor sit amet consectetur adipisicing elit. Quia cumque
                deserunt necessitatibus minima porro molestias, enim provident,
                praesentium sequi voluptatibus voluptatem culpa quisquam
                adipisci ipsam. Voluptates quibusdam veniam et laborum?
              </p>
            </div>
          </swiper-slide>
          <swiper-slide
            ><div class="swiper-box">
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Consequatur nostrum dolorem eum inventore? Maiores molestiae
                nisi iure assumenda alias, facere architecto esse quasi
                similique? Magni molestiae repellat sunt pariatur et! Lorem
                ipsum dolor sit amet consectetur adipisicing elit. Quia cumque
                deserunt necessitatibus minima porro molestias, enim provident,
                praesentium sequi voluptatibus voluptatem culpa quisquam
                adipisci ipsam. Voluptates quibusdam veniam et laborum?
              </p>
            </div>
          </swiper-slide>
          <swiper-slide
            ><div class="swiper-box">
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Consequatur nostrum dolorem eum inventore? Maiores molestiae
                nisi iure assumenda alias, facere architecto esse quasi
                similique? Magni molestiae repellat sunt pariatur et! Lorem
                ipsum dolor sit amet consectetur adipisicing elit. Quia cumque
                deserunt necessitatibus minima porro molestias, enim provident,
                praesentium sequi voluptatibus voluptatem culpa quisquam
                adipisci ipsam. Voluptates quibusdam veniam et laborum?
              </p>
            </div>
          </swiper-slide>
          <swiper-slide
            ><div class="swiper-box">
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Consequatur nostrum dolorem eum inventore? Maiores molestiae
                nisi iure assumenda alias, facere architecto esse quasi
                similique? Magni molestiae repellat sunt pariatur et! Lorem
                ipsum dolor sit amet consectetur adipisicing elit. Quia cumque
                deserunt necessitatibus minima porro molestias, enim provident,
                praesentium sequi voluptatibus voluptatem culpa quisquam
                adipisci ipsam. Voluptates quibusdam veniam et laborum?
              </p>
            </div>
          </swiper-slide>
          <swiper-slide
            ><div class="swiper-box">
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Consequatur nostrum dolorem eum inventore? Maiores molestiae
                nisi iure assumenda alias, facere architecto esse quasi
                similique? Magni molestiae repellat sunt pariatur et! Lorem
                ipsum dolor sit amet consectetur adipisicing elit. Quia cumque
                deserunt necessitatibus minima porro molestias, enim provident,
                praesentium sequi voluptatibus voluptatem culpa quisquam
                adipisci ipsam. Voluptates quibusdam veniam et laborum?
              </p>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
    <div class="spacer-10 bg-light"></div>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper";
import "swiper/css";
import "swiper/css/pagination";
export default {
  components: { Swiper, SwiperSlide },
  setup() {
    const onSwiper = (swiper) => {
      console.log(swiper);
    };
    const onSlideChange = () => {
      console.log("slide change");
    };
    return {
      onSwiper,
      onSlideChange,
      modules: [Pagination],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "src/public/assets/scss/_variables.scss";
.no-parallax {
  position: relative;
  z-index: 2;
  min-height: fit-content;
  // min-height: 100vh;
  transform-style: preserve-3d;
  // @media (orientation: landscape) and (min-width: 1400px) {
  //   min-height: 70vh;
  // }
  // @media (orientation: landscape) and (max-width: 1400px) {
  //   min-height: 60vh;
  // }
  // @media (orientation: landscape) and (max-width: 1200px) {
  //   min-height: 80vh;
  // }
  // @media (orientation: portrait) and (max-width: 1200px) {
  //   min-height: 50vh;
  // }
  // @media (orientation: landscape) and (max-width: 992px) {
  //   min-height: 40vh;
  // }
  // @media (orientation: landscape) and (max-width: 768px) {
  //   min-height: 70vh;
  // }
  // @media (orientation: portrait) and (max-width: 1200px) {
  //   min-height: 50vh;
  // }
  // @media (orientation: landscape) and (max-width: 578px) {
  //   min-height: 120vh;
  // }
  // @media (max-height: 500px) and (orientation: landscape) {
  //   min-height: 140vh;
  // }
}
.spacer-10 {
  position: relative;
}

.orange::after {
  content: "";
  background: $secondary;
  height: 50%;
  width: 90%;
  top: 0;
  left: -5vw;
  position: absolute;
}
.swiper-container {
  padding: 1rem;
  display: flex;
  flex-basis: 90%;
  background: white;
  border-radius: 3px;
  @media (max-width: 576px) {
    padding: 0.5rem;
    padding-bottom: 2rem;
    margin-left: 0.5rem;
    margin-right: 0.5rem;
    margin-top: 1rem;
  }
}

.mySwiper {
  margin-bottom: 1rem;
  z-index: 5;
  text-align: center;
  @media (max-width: 576px) {
    // min-height: 75vh;
  }
  @media (orientation: landscape) and (min-width: 1400px) {
    margin-bottom: 2rem;
  }
}

.swiper-slide {
  display: flex;
  justify-content: center;
}

.swiper-box {
  padding: 1rem;
  outline: none;
  border: 0.2em black solid;
  margin-bottom: 1rem;
  // height: 95%;
  height: fit-content;
  width: 90%;
  box-shadow: -1em 1em 0em rgba($info, 0.6);
  @media (max-width: 576px) {
    box-shadow: -0.75em 0.75em 0em rgba($info, 0.6);
  }
}
</style>
