<template>
  <div>
    <div id="carouselExampleDark" class="carousel carousel-dark slide">
      <div class="carousel-indicators">
        <button
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide-to="0"
          class="active"
          aria-current="true"
          aria-label="Slide 1"
        ></button>
        <button
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide-to="1"
          aria-label="Slide 2"
        ></button>
        <button
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide-to="2"
          aria-label="Slide 3"
        ></button>
      </div>
      <div class="carousel-inner">
        <div class="carousel-item active" data-bs-interval="10000">
          <div class="row">
            <div class="col-1"></div>
            <div class="col-4 text-container">
              <h2>{{ cycle1.Brand }}</h2>
              <h4>{{ cycle1.Model }}</h4>
              <p class="d-none d-md-block">
                {{ cycle1.Description.slice(0, 150) }} .....
              </p>
              <button
                type="button"
                class="btn btn-outline-dark"
                v-on:click="view(cycle1._id)"
              >
                More Details
              </button>
            </div>
            <div class="col-6">
              <img
                v-bind:src="cycle1.Image"
                class="d-block container"
                id="photo"
              />
            </div>
            <div class="col-1"></div>
          </div>
        </div>
        <div class="carousel-item" data-bs-interval="2000">
          <div class="row">
            <div class="col-1"></div>
            <div class="col-4 text-container">
              <h2>{{ cycle2.Brand }}</h2>
              <h4>{{ cycle2.Model }}</h4>
              <p class="d-none d-md-block">
                {{ cycle2.Description.slice(0, 150) }} .....
              </p>
              <button
                type="button"
                class="btn btn-outline-dark"
                v-on:click="view(cycle2._id)"
              >
                More Details
              </button>
            </div>
            <div class="col-6 text-center">
              <img
                v-bind:src="cycle2.Image"
                class="d-block container"
                id="photo"
              />
            </div>
            <div class="col-1"></div>
          </div>
        </div>
        <div class="carousel-item">
          <div class="row">
            <div class="col-1"></div>
            <div class="col-4 text-container">
              <h2>{{ cycle3.Brand }}</h2>
              <h4>{{ cycle3.Model }}</h4>
              <p class="d-none d-md-block">
                {{ cycle3.Description.slice(0, 150) }} .....
              </p>
              <button
                type="button"
                class="btn btn-outline-dark"
                v-on:click="view(cycle3._id)"
              >
                More Details
              </button>
            </div>
            <div class="col-6">
              <img
                v-bind:src="cycle3.Image"
                class="d-block container"
                id="photo"
              />
            </div>
            <div class="col-1"></div>
          </div>
        </div>
      </div>

      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carouselExampleDark"
        data-bs-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carouselExampleDark"
        data-bs-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API_URL = "https://assignment2.eicot.repl.co";
export default {
  name: "ShowCycle",
  data: function () {
    return {
      cycle1: "",
      cycle2: "",
      cycle3: "",
      choosenNumber: new Set(),
    };
  },

  mounted: async function () {
    let response = await axios.get(API_URL + "/specification");
    this.allCycles = response.data;
    // this.show1();
    // this.show2();
    // this.show3();
    this.show();
  },

  methods: {
    // show1: function () {
    //   const chooseNumber = Math.floor(Math.random() * this.allCycles.length);
    //   this.cycle1 = this.allCycles[chooseNumber];
    // },
    // show2: function () {
    //   const chooseNumber = Math.floor(Math.random() * this.allCycles.length);
    //   this.cycle2 = this.allCycles[chooseNumber];
    // },
    // show3: function () {
    //   const chooseNumber = Math.floor(Math.random() * this.allCycles.length);
    //   this.cycle3 = this.allCycles[chooseNumber];
    // },
    view: function (cycleId) {
      this.$parent.$emit("view-cycle", cycleId);
    },
    selectNumber: function () {
      return Math.floor(Math.random() * this.allCycles.length);
    },
    show: function () {
      while (this.choosenNumber.size < 3) {
        const newNumber = this.selectNumber();
        this.choosenNumber.add(this.allCycles[newNumber]);
      }
      const newCycle = Array.from(this.choosenNumber);
      this.cycle1 = newCycle[0];
      this.cycle2 = newCycle[1];
      this.cycle3 = newCycle[2];
    },
  },
};
</script>

<style scoped>
.text-container {
  text-align: center;
}

#photo {
  height: 450px;
  position: left;
}
</style>