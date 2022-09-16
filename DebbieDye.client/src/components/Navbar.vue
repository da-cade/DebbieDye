<template>
  <nav class="navbar sticky-top navbar-expand-lg navbar-dark">
    <div class="container-fluid nav-container">
      <button
        @click="toggleStyle"
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#myNavbar"
        aria-controls="myNavbar"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="float">
        <a class="debbie" @click="$emit('scroll', 'Landing')"
          ><h2 class="mb-0">Debbie Dye</h2></a
        >
      </div>
      <div
        ref="collapse"
        class="collapse navbar-collapse justify-content-md-around"
        id="myNavbar"
      >
        <ul class="navbar-nav">
          <li class="nav-item mx-md-5">
            <a class="nav-link" @click="$emit('scroll', 'Bio')">About Me</a>
          </li>
          <li class="nav-item mx-md-5">
            <a class="nav-link" @click="$emit('scroll', 'Services')"
              >Services</a
            >
          </li>
        </ul>
        <ul class="navbar-nav">
          <li class="nav-item mx-md-5">
            <a class="nav-link" @click="$emit('scroll', 'Reviews')">Reviews</a>
          </li>
          <li class="nav-item mx-md-5">
            <a class="nav-link" href="#">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>


<script>
import { onMounted, ref, watchEffect } from "@vue/runtime-core";
export default {
  setup() {
    const collapse = ref(null);
    const menuShowing = ref(false);
    const navShowing = ref(false);
    const fadeOut = ref("");

    function toggleStyle() {
      menuShowing.value = !menuShowing.value;
      let items = document.querySelectorAll(".nav-link");
      if (!items[items.length - 1].classList.contains("opaque")) {
        for (let i = 0; i < items.length; i++) {
          const item = items[i];
          setTimeout(() => {
            item.classList.add("opaque");
          }, 75 * i);
        }
      } else {
        for (let i = 0; i < items.length; i++) {
          const item = items[i];
          item.classList.remove("opaque");
        }
      }
    }

    watchEffect(() => {
      let nav = document.querySelector(".navbar");
      navShowing.value;
      menuShowing.value;
      if (nav) {
        if (navShowing.value && !menuShowing.value) {
          fadeOut.value = setTimeout(() => {
            nav.classList.remove("opaque");
          }, 4000);
        }
        if (navShowing.value && menuShowing.value) {
          clearTimeout(fadeOut.value);
        }
      }
    });

    onMounted(() => {
      let main = document.querySelector("main");
      let prevScrollpos = main.scrollTop;
      let nav = document.querySelector(".navbar");
      main.onscroll = function () {
        let currentScrollPos = main.scrollTop;
        if (prevScrollpos > currentScrollPos) {
          // @ts-ignore
          nav.classList.add("navbar_show");
          nav.classList.add("opaque");
          navShowing.value = true;
        } else {
          // @ts-ignore
          nav.classList.remove("navbar_show");
          nav.classList.remove("opaque");
          navShowing.value = false;
        }
        prevScrollpos = currentScrollPos;
      };
    });
    return {
      collapse,
      toggleStyle,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "src/public/assets/scss/_variables.scss";

.navbar {
  min-height: 60px;
  background-color: #5d0149;
  transform: translate3d(0, -110%, 0);
  transition: transform 0.2s ease-out, background-color 0.4s ease-out 0.15s;
  @media (max-width: 576px) {
    min-height: 5rem;
  }
}

.opaque {
  @media (max-width: 576px) {
    background-color: rgba(255, 255, 255, 0.171) !important;
  }
}

.navbar_show {
  transform: translate3d(0, 0, 0);
}

.nav-container {
  position: relative;
  display: flex;
  justify-content: start;
}

.float {
  z-index: 10;
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.debbie {
  h2 {
    margin-top: 0.5rem;
    font-family: "nycd";
    font-size: 3rem;
    color: white;
    @media (max-width: 576px) {
      color: black;
    }
  }
}

ul {
  z-index: 11;
}

a:hover {
  cursor: pointer;
}

@media (max-width: 576px) {
  .navbar {
    background: transparent;
  }
  .navbar-collapse {
    position: absolute;
    left: 0;
    top: 4.5rem;
    z-index: 100;
  }
  .float {
    position: static;
    width: auto;
    height: auto;
  }
  .nav-link {
    color: rgba(0, 0, 0, 0.774) !important;
    padding-left: 0.5rem;
    padding-right: 45vw;
  }

  .debbie {
    padding-left: 1rem;
  }
}
</style>
