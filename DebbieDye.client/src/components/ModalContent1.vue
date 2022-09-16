<template>
  <div class="container">
    <div class="row backsplash">
      <div class="hold-2 mb-5">
        <h2 class="p-2">CONTRACT TO CLOSE CHECKLIST</h2>
      </div>
      <!-- <div class="buyer-cols col-md-5">
        <div class="row"> -->
      <div class="col-md-5">
        <div class="section section-1">
          <p>
            <span>1.</span>First, all documents and MLS information for the
            property are verified.
          </p>
          <p>
            <span>2.</span>A digital folder is created in Google Drive to easily
            share files.
          </p>
          <p><span>3.</span>Introductions emails go out to all parties.</p>

          <!-- <div class="arrow-line-1">
            <div class="arrow"></div>
          </div> -->
          <div class="svgCanvas svg-0">
            <svg id="svg-0" xmlns="http://www.w3.org/2000/svg"></svg>
          </div>
        </div>
      </div>
      <div class="col-md-5">
        <div class="section section-2">
          <p>
            <span>4.</span>All requisite documents are uploaded to the
            transaction management system.
          </p>
          <p>
            <span>5.</span>Earnest money and receipts are requested from the
            relevant parties. This is uploaded and sent to all parties.
          </p>
          <p>
            <span>6.</span> Title Commitment is reviewed and sent to the buyer
            for review.
          </p>
          <!-- <div class="arrow-line-2">
            <div class="arrow"></div>
          </div> -->
          <div class="svgCanvas svg-1">
            <svg id="svg-1" xmlns="http://www.w3.org/2000/svg"></svg>
          </div>
        </div>
      </div>
      <div class="col-md-5">
        <div class="section section-3">
          <p>
            <span>8.</span>
            The agent is reminded the day before the due date of the RE-10
            Inspection Report.
          </p>
          <p>
            <span>9.</span>Repairs and credits are noted and the RE10 is sent to
            lender and title if the sale price changes.
          </p>
          <p>
            <span>10.</span> Information about utilites are sent to the buyer.
          </p>

          <div class="svgCanvas svg-2">
            <svg id="svg-2" xmlns="http://www.w3.org/2000/svg"></svg>
          </div>
        </div>
      </div>
      <div class="col-md-5">
        <div class="section section-4">
          <p>
            <span>10.</span>The settlement statement is reviewed for accuracy by
            two sets of eyes, and is signed and uploaded to the transaction
            management system.
          </p>

          <p>
            <span>12.</span>Commission checks are uploaded, the property folder
            in Drive is considered closed and is archived for 1 year.
          </p>

          <div class="svgCanvas svg-3">
            <svg id="svg-3" xmlns="http://www.w3.org/2000/svg"></svg>
          </div>
        </div>
      </div>
      <div class="spacer-20"></div>
    </div>
  </div>
</template>

<script>
import { onMounted } from "@vue/runtime-core";
export default {
  setup() {
    onMounted(() => {
      const sections = document.querySelectorAll(".section");

      let pointList = [];
      for (let i = 0; i < sections.length; i++) {
        const s = sections[i];
        const rect = s.getBoundingClientRect();
        let top;
        switch (i) {
          case 0:
            top = 0;
            break;
          case 1:
            top = rect.height * 0.25;
            break;
          case 2:
            top = rect.height * 0.15;
            break;
          case 3:
            top = rect.height * 0.35;
            break;
        }
        s.style.top = top + "px";
        const point = { x: 0, y: 0 };
        if (
          s.className.includes("section-2") ||
          s.className.includes("section-4")
        ) {
          point.x = rect.left;
        } else {
          point.x = rect.left + rect.width - 3;
        }
        point.y = s.offsetTop + rect.height / 2;
        pointList.push(point);
      }

      for (let i = 0; i < pointList.length - 1; i++) {
        const point = pointList[i];
        console.log(pointList[i]);

        let svgElem = document.getElementById("svg-" + i);
        console.log(svgElem);
        let side1 = Math.abs(pointList[i + 1].y - point.y);
        let side2 = Math.abs(pointList[i + 1].x - point.x);
        let hypoteneus = Math.sqrt(Math.pow(side1, 2) + Math.pow(side2, 2));
        let angle = Math.acos(side1 / hypoteneus) * (180 / Math.PI);

        svgElem.style.position = "absolute";
        svgElem.style.top = 50 + "%";

        if (i == 1 || i == 3) {
          svgElem.style.left = 0;
          svgElem.style.transform = `rotate(${angle}deg)`;
        } else {
          svgElem.style.right = 0;
          svgElem.style.transform = `rotate(-${angle}deg)`;
        }
        svgElem.style.transformOrigin = "top";
        svgElem.setAttribute("height", hypoteneus);
        svgElem.setAttribute("className", "svgCanvas");
        svgElem.setAttribute("width", "4px");
        svgElem.setAttribute("id", `svg-${i}`);

        let newLine = document.createElementNS(
          "http://www.w3.org/2000/svg",
          "line"
        );
        newLine.setAttribute("stroke", "#d66e00");
        newLine.setAttribute("id", "svgLine-" + i);
        newLine.setAttribute("stroke-width", "4");
        newLine.setAttribute("x1", "0");
        newLine.setAttribute("y1", "0");
        newLine.setAttribute("x2", "100%");
        newLine.setAttribute("y2", "100%");

        svgElem.appendChild(newLine);
        setTimeout(() => {
          newLine.classList.add("dashAnimation");
        }, 1000 * i);
      }
    });
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import "src/public/assets/scss/_variables.scss";
.container {
  overflow: hidden;
}

.backsplash {
  position: relative;
  display: flex;
  padding: 2rem;
  justify-content: space-around;
  z-index: 10;
  border-left: 0.2em $secondary solid;
  border-right: 0.2em $secondary solid;
}
.backsplash::after {
  content: "";
  z-index: -2;
  position: absolute;
  background: darken($light, 5);
  top: 5%;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 5px;
}

.hold-2 {
  z-index: 12;
  display: flex;
  flex: 1 0 auto;
  flex-direction: column;
  max-width: 100%;
  background-color: #fff;
  padding: 1em;
  outline: none;
  border: 0.2em black solid;
  justify-content: space-between;
  transition: ease 0.25s;
  @media (max-height: 500px) and (orientation: landscape) {
    max-width: none;
  }
  @media (orientation: portrait) and (max-width: 578px) {
    max-width: none;
  }
  box-shadow: 1em 1em 0em rgba($info, 0.6);
}

.buyer-cols {
  z-index: 12;
}

.backsplash .col-md-5 {
  display: flex;
  flex-direction: column;
}

.section {
  position: relative;
  @media (max-width: 768px) {
    position: static;
  }
  background: lighten($light, 5);
  display: flex;
  flex-direction: column;
  flex: 1 0 auto;
  max-width: 100%;
  margin: 0.5rem;
  padding: 1rem;
  border-radius: 8px;
}

.svgCanvas {
  z-index: -1;
  position: absolute;
  inset: 0;
}

.arrow-line-1,
.arrow-line-2,
.arrow-line-3 {
  border-top: 3px solid $secondary;
  position: absolute;
  height: 3px;
  background: none 0px 0px transparent;
  z-index: -1;
  display: block;
  @media (max-width: 767px) {
    display: none;
  }
}

.arrow-line-1,
.arrow-line-3 {
  top: 50%;
  right: 0;
  -webkit-animation: slideright 2s forwards;
  -moz-animation: slideright 2s forwards;
  -o-animation: slideright 2s forwards;
  animation: slideright 2s forwards;
  transform: translateX(100%) rotate(25deg) translateX(0);
  -moz-transform: translateX(100%) rotate(25deg) translateX(0);
  -webkit-transform: translateX(100%) rotate(25deg) translateX(0);
  -webkit-transform-origin: 0 0;
  -moz-transform-origin: 0 0;
  transform-origin: 0 0;
}

.arrow-line-2 {
  top: 50%;
  -webkit-animation: slideleft 2s forwards;
  -moz-animation: slideleft 2s forwards;
  -o-animation: slideleft 2s forwards;
  animation: slideleft 2s forwards;
  -moz-transform: rotate(-245deg);
  -webkit-transform: rotate(-245deg);
  transform: rotate(-245deg);
  -webkit-transform-origin: 0 0;
  -moz-transform-origin: 0 0;
  transform-origin: 0 0;
}

.arrow {
  position: absolute;
  display: block;
  left: 50%;
}
.arrow::before,
.arrow::after {
  content: "";
  position: absolute;
  display: block;
  height: 3px;
  width: 2rem;
  left: 50%;
  top: -3px;
  background: $secondary;
  transform-origin: 100% 100%;
}

.arrow::before {
  animation: fold-out-right 0.5s ease-in 0.5s forwards;
}

.arrow::after {
  animation: fold-out-left 0.5s ease-in 0.5s forwards;
}

@keyframes fold-out-right {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(45deg);
  }
}
@keyframes fold-out-left {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-45deg);
  }
}

@keyframes slideleft {
  from {
    width: 0;
  }

  to {
    width: 30vmin;
  }
}
@keyframes slideright {
  from {
    width: 0;
  }

  to {
    width: 12vmin;
  }
}

.section-1::after,
.section-2::after,
.section-3::after,
.section-4::after {
  position: absolute;
  content: "";
  background: $light;
  height: 100%;
  width: 100%;
  z-index: -1;
  border-radius: 8px;
}

.section-1::after {
  top: -5%;
  left: -5%;
}
.section-2::after {
  top: -5%;
  right: -5%;
}
.section-3::after {
  bottom: -5%;
  left: -5%;
}
.section-4::after {
  bottom: -5%;
  right: -5%;
}

.section span {
  margin-right: 10px;
}

.modal-section-picker {
  padding: 1em;
  border-bottom: 5px rgba($secondary, 01) solid;
  text-align: center;
}
.modal-section-picker-2 {
  position: absolute;
  width: 100%;
  top: 40%;
  right: 52%;
  height: 20%;
  rotate: 90deg;
  background-color: white;
  padding: 2em;
  opacity: 0;
}

ul {
  font-size: 0.8em;
}
.hold {
  position: absolute;
  width: 50%;
  top: 40%;
  height: 20%;
  rotate: 90deg;
  transition: all 0.7s;
  left: 65%;
  background-color: rgba($light, 1);
}

.other-text {
  opacity: 0;
  transition: all 0.1s;
  transition-delay: 0.1s;
  transform: translateY(-10%);
  padding-left: 3em;
}

.holderr {
  z-index: 15;
}

.holderr:hover {
  .hold {
    rotate: 0deg;
    top: 0;
    left: 12%;
    height: 100%;
    transition: all 0.7s;
    padding: 2em;
    width: 100%;
  }

  .other-text {
    opacity: 1;
    transition: all 0.7s;
    transform: translateY(0);
  }
  .modal-section-picker {
    border-bottom: 5px transparent solid;
    text-align: start;
  }
  .modal-section-picker-2 {
    border-top: 5px rgba($secondary, 01) solid;
    opacity: 1;
    left: -30%;
    width: 50%;
    text-align: center;
  }
}
</style>
