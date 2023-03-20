<template>
  <div>
    <ShowCycle />
    <div class="row mb-2 navbar">
      <div class="col-sm-3">
        <select class="form-select" v-model="searchByBrand">
          <option value="">All Brands</option>
          <option value="BMW">BMW</option>
          <option value="Ducati">Ducati</option>
          <option value="Harley-Davidson">Harley-Davidson</option>
          <option value="Honda">Honda</option>
          <option value="Indian">Indian</option>
          <option value="KTM">KTM</option>
          <option value="Suzuki">Suzuki</option>
          <option value="Triumph">Triumph</option>
          <option value="Vespa">Vespa</option>
          <option value="Yamaha">Yamaha</option>
        </select>
      </div>
      <div class="col-sm-3">
        <select class="form-select" v-model="searchByType">
          <option value="">All Types</option>
          <option value="Classic">Classic</option>
          <option value="Enduro / offroad">Enduro / offroad</option>
          <option value="Naked bike">Naked Bike</option>
          <option value="Scooter">Scooter</option>
          <option value="Sport">Sport</option>
          <option value="Touring">Touring</option>
        </select>
      </div>
      <div class="col-sm-3">
        <select class="form-select" v-model="searchByYear">
          <option value="">All Years</option>
          <option value="2022">2022</option>
          <option value="2021">2021</option>
          <option value="2020">2020</option>
          <option value="2019">2019</option>
          <option value="2018">2018</option>
          <option value="2017">2017</option>
        </select>
      </div>

      <div class="col-sm-3">
        <input
          type="text"
          class="form-control"
          v-model="search"
          placeholder="Search Cycle"
        />
      </div>
    </div>

    <div class="row card-container">
      <div
        class="card text-center btn btn-outline-dark"
        v-on:click="view(c._id)"
        style="width: 20rem"
        v-for="(c, index) in filteredCycles"
        v-bind:key="index"
      >
        <img class="container" v-bind:src="c.Image" id="photo" />
        <div class="card-body">
          <h5 class="card-title">{{ c.Brand }} {{ c.Model }}</h5>
          <p class="card-text-center">{{ c.Category }} {{ c.Year }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ShowCycle from "@/components/ShowCycle.vue";
const API_URL = "https://assignment2.eicot.repl.co";
export default {
  name: "Home",
  components: {
    ShowCycle,
  },
  data: function () {
    return {
      allCycles: [],
      search: "",
      searchByBrand: "",
      searchByType: "",
      searchByYear: "",
    };
  },
  mounted: async function () {
    let response = await axios.get(API_URL + "/specification");
    this.allCycles = response.data;
  },
  methods: {
    view: function (cycleId) {
      this.$emit("view-cycle", cycleId);
    },
  },
  computed: {
    filteredCycles: function () {
      let filteredCycle = [];

      for (let eachCycle of this.allCycles) {
        if (
          eachCycle.Brand.includes(this.searchByBrand) &&
          eachCycle.Category.includes(this.searchByType) &&
          eachCycle.Year.toString().includes(this.searchByYear.toString()) &&
          (eachCycle.Brand.toLowerCase().includes(this.search.toLowerCase()) ||
            eachCycle.Model.toLowerCase().includes(this.search.toLowerCase()))
        ) {
          filteredCycle.push(eachCycle);
        }
      }

      return filteredCycle;
    },
  },
  emits: ["view-cycle"], //declare emits here to App.vue
};
</script>

<style scoped>
.card-container {
  display: flex;
  justify-content: space-evenly;
}

.card {
  margin-bottom: 20px;
}

#photo {
  height: 200px;
}

.navbar {
  background-color: rgb(0, 0, 0);
  border-radius: 5px;
  margin: 5px;
}
</style>
