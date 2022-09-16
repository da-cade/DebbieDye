<template>
  <div class="container-fluid no-parallax bg-light">
    <div class="row main-row">
      <div class="back-square"></div>
      <div
        class="
          col-12
          d-flex
          justify-content-center
          align-items-center
          section-header
        "
      >
        <div class="text-center">
          <h2 class="" v-scrollanimation>
            Over 14 yrs experience as a Real Estate Transaction Coordinator
          </h2>

          <p class="fs-4 text-secondary" v-scrollanimation>
            I enjoy assisting agents with the details of their transactions, so
            they can be out doing what they love.
          </p>
        </div>
      </div>
      <div class="col-12 image-holder">
        <img
          src="../public/assets/img/debbie-removebg-preview-2.png"
          alt="debbie headshot image"
          class="head-img"
        />
        <div class="card card-1">
          <p class="p-4 fs-4" v-scrollanimation>
            I believe my background in mortgage lending has given me an
            advantage to understand the full process of what takes place from
            contract to closing on all levels.
          </p>
        </div>
      </div>

      <div class="col-12 bio-holder">
        <div class="container">
          <p class="">
            I was a realtor when I realized that my gifts lay in taking care of
            all the details of the transaction. I was working with an agency
            when an opportunity arose for me to become an underwriting assistant
            for a wholesale lender, and I leaned in. I asked a lot of questions
            and learned what an underwriters and agents needed behind the
            scenes. After about 6 months, I transitioned into a loan processor
            and within a couple of years my manager asked me to pick up more and
            more transaction responsibilities, such as
            <strong>underwriting, proccesses, and closing</strong>. One of my
            specialties was in FHA 203k rehab loans, an ugly process that most
            of my colleagues avoided — but I took them on.
            <strong>I always enjoy a challenge.</strong>
            <br />
            <br />
            In my free time, I like to golf, play cards with my friends and
            family, and I even just recently started doing watercolor painting
            with my grandchildren!
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted } from "@vue/runtime-core";
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import "src/public/assets/scss/_variables.scss";

.no-parallax {
  z-index: 2;
  transform-style: preserve-3d;
  position: relative;
  // min-height: 120vh;
  min-height: fit-content;
  @media (min-width: 1400px) {
    // min-height: 100vh;
  }
  @media (max-width: 576px) {
    // min-height: 180vh;
  }
  @media (orientation: landscape) and (max-width: 700px) {
    min-height: 300vh;
  }
}

.main-row {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  @media (max-width: 576px) {
    // height: 200%;
  }
  @media (orientation: landscape) {
    // height: 200vh;
  }
}

.back-square {
  z-index: 1;
  height: 100vh;
  width: 100vw;
  position: absolute;
  background: rgba($light, 1);
  @media (max-width: 576px) {
    // height: 140%;
  }
  @media (orientation: landscape) {
    // height: 170%;
  }
}

.back-square::after,
.back-square::before {
  content: "";
  border-left: 2.5vh transparent solid;
  border-right: 2.5vh transparent solid;
  position: absolute;
  width: 50%;
  z-index: -1;
  top: -5%;
}

.back-square::before {
  border-bottom: 50.8vw solid rgba($light, 1);
  rotate: 270deg;
  left: -1px;
}
.back-square::after {
  border-top: 50.8vw solid rgba($light, 1);
  rotate: -90deg;
  right: -1px;
}

.section-header {
  z-index: 2;
}
.section-header div {
  @media (min-width: 992px) {
    padding-left: 5%;
    padding-right: 5%;
  }
}

.image-holder {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  // height: 30%;
  margin-bottom: 10em;
  @media (max-width: 600px) {
    margin-bottom: 10em;
  }
}

.image-holder::after {
  content: "";
  position: absolute;
  z-index: 1;
  align-self: center;
  top: 20%;
  right: 5%;
  background: darken($light, 10);
  border-radius: 10px;
  height: 105%;
  width: 40%;
}

.head-img {
  z-index: 5;
  position: relative;
  padding-right: 2em;
  width: 20vw;
  @media (max-width: 900px) {
    z-index: 3;
    width: 30vw;
  }
  @media (max-width: 600px) {
    z-index: 3;
    width: 65vw;
  }
}

.head-img::after .card {
  border-radius: 0px;
  z-index: 5;
  outline: none;
  background: rgba($light, 1);
  border: 0em black solid;
}

.card-1 {
  position: absolute;
  border-radius: 2.5px;
  background: rgba($light, 1);
  z-index: 10;
  border-right: 0.1em rgba(0, 0, 0, 0.528) solid;
  border-top: 0.1em rgba(0, 0, 0, 0.587) solid;
  box-shadow: -20vw 2em 0em rgba($info, 0.6);
  width: 40vw;
  font-size: 1.1em;
  top: 15em;
  @media (max-width: 600px) {
    width: 85vw;
  }
}

.bio-holder {
  z-index: 5;
  margin-bottom: 2em;
  p {
    padding: 5rem;
  }
  @media (max-width: 1400px) {
    margin-top: 5em;
  }
  @media (max-width: 1200px) {
    margin-top: 5em;
  }
  @media (max-width: 900px) {
    margin-top: 5em;
  }
  @media (max-width: 600px) {
    margin-bottom: 2em;
    margin-top: 10em;
    p {
      padding: 0;
    }
  }
  @media (orientation: landscape) {
  }
}

h2 {
  margin-top: 1em;
  font-size: 2.5em;
  font-family: "Unna", serif;
}
</style>
