<template>
  <div>
    <div class="row">
      <div class="col-1"></div>
      <div class="col-10">
        <div class="row">
          <img class="col-5" v-bind:src="allCycles.Image" id="photo" />
          <p class="col-7" container-fluid>
            {{ allCycles.Description }}
          </p>
        </div>
        <div class="row">
          <div class="col-8">
            <h1>{{ allCycles.Brand }} {{ allCycles.Model }}</h1>
          </div>
          <div class="col-4">
            <button
              type="button"
              class="btn btn-outline-dark"
              v-on:click="edit(cycleId)"
            >
              Edit
            </button>
            <button
              type="button"
              class="btn btn-outline-dark"
              v-on:click="remove(cycleId)"
            >
              Delete
            </button>
          </div>
        </div>
        <div class="row"></div>
        <table class="action_table">
          <tbody>
            <tr class="blank_row">
              <td colspan="2">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2"><h5>General Information</h5></td>
            </tr>
            <tr class="data_row">
              <td>Brand:</td>
              <td>{{ allCycles.Brand }}</td>
            </tr>
            <tr class="data_row">
              <td>Model:</td>
              <td>{{ allCycles.Model }}</td>
            </tr>
            <tr class="data_row">
              <td>Type:</td>
              <td>{{ allCycles.Category }}</td>
            </tr>
            <tr class="data_row">
              <td>Year:</td>
              <td>{{ allCycles.Year }}</td>
            </tr>
            <tr>
              <td>Colors Available:</td>
              <td>
                {{ allCycles.ColorOptions.join(", ") }}
              </td>
            </tr>
            <tr class="blank_row">
              <td colspan="2">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2">
                <h5>Engine and Transmission Specifications</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td>Bore:</td>
              <td>{{ allCycles.Engine.Bore_mm }} mm</td>
            </tr>
            <tr class="data_row">
              <td>Cooling System:</td>
              <td>{{ allCycles.Engine.CoolingSystem }}</td>
            </tr>
            <tr class="data_row">
              <td>Cylinder:</td>
              <td>{{ allCycles.Engine.Cylinder }}</td>
            </tr>
            <tr class="data_row">
              <td>Displacement:</td>
              <td>{{ allCycles.Engine.Displacement_ccm }} ccm</td>
            </tr>
            <tr class="data_row">
              <td>Gearbox:</td>
              <td>{{ allCycles.Engine.Gearbox }}</td>
            </tr>
            <tr class="data_row">
              <td>Power:</td>
              <td>{{ allCycles.Engine.Power_hp }} hp</td>
            </tr>
            <tr class="data_row">
              <td>Stroke:</td>
              <td>{{ allCycles.Engine.Stroke }}</td>
            </tr>
            <tr class="data_row">
              <td>Torque:</td>
              <td>{{ allCycles.Engine.Torque_Nm }} Nm</td>
            </tr>
            <tr class="data_row">
              <td>Transmission Type:</td>
              <td>{{ allCycles.Engine.TransmissionType }}</td>
            </tr>

            <tr class="blank_row">
              <td colspan="2">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2">
                <h5>Fuel System</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td>Fuel Capacity:</td>
              <td>{{ allCycles.Fuel.Capacity_lts }} lts</td>
            </tr>
            <tr class="data_row">
              <td>Fuel Control:</td>
              <td>{{ allCycles.Fuel.Control }}</td>
            </tr>
            <tr class="data_row">
              <td>Fuel System:</td>
              <td>{{ allCycles.Fuel.System }}</td>
            </tr>

            <tr class="blank_row">
              <td colspan="2">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2">
                <h5>Dimension and Brake System</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td>Weight:</td>
              <td>{{ allCycles.Physical.DryWeight_kg }} kg</td>
            </tr>
            <tr class="data_row">
              <td>Seat Height:</td>
              <td>{{ allCycles.Physical.SeatHeight_mm }} mm</td>
            </tr>
            <tr class="data_row">
              <td>Wheelbase:</td>
              <td>{{ allCycles.Physical.Wheelbase_mm }} mm</td>
            </tr>
            <tr class="data_row">
              <td>Front Brakes:</td>
              <td>{{ allCycles.Wheel.FrontBrakes }}</td>
            </tr>
            <tr class="data_row">
              <td>Rear Brakes:</td>
              <td>{{ allCycles.Wheel.RearBrakes }}</td>
            </tr>
            <tr class="data_row">
              <td>Front Suspension:</td>
              <td>{{ allCycles.Wheel.FrontSuspension }}</td>
            </tr>
            <tr class="data_row">
              <td>Rear Suspension:</td>
              <td>{{ allCycles.Wheel.RearSuspension }}</td>
            </tr>
            <tr class="data_row">
              <td>Front Tire:</td>
              <td>{{ allCycles.Wheel.FrontTire }}</td>
            </tr>
            <tr class="data_row">
              <td>Rear Tire:</td>
              <td>{{ allCycles.Wheel.RearTire }}</td>
            </tr>
            <tr class="blank_row">
              <td colspan="3">&nbsp;</td>
            </tr>
          </tbody>
        </table>
        <div class="row mb-3">
          <label class="col-form-label">Reviews: </label>
          <ul>
            <li v-for="(r, index) in allCycles.Reviews" :key="index">
              {{ r }}
            </li>
          </ul>
        </div>
        <div class="row mb-3">
          <label class="col-sm col-form-label">Add Review: </label>
          <div class="col-1">
            <button
              type="button"
              class="btn btn-outline-dark"
              v-on:click="addReview(cycleId)"
            >
              Add
            </button>
          </div>
          <div class="col-12">
            <textarea
              type="text"
              class="form-control"
              v-model="Reviews"
              rows="2"
            ></textarea>
          </div>
        </div>
      </div>
      <div class="col-1"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API_URL = "https://assignment2.eicot.repl.co";
export default {
  name: "Specification",
  data: function () {
    return {
      allCycles: "",
      Reviews: [],
    };
  },
  props: ["cycleId"], //receive cycleId information from App.vue
  mounted: async function () {
    let response = await axios.get(API_URL + "/specification/" + this.cycleId);
    this.allCycles = response.data;
    this.Reviews = response.data.Reviews;
  },

  methods: {
    edit: function (cycleId) {
      this.$emit("edit-cycle", cycleId);
    },
    remove: async function (cycleId) {
      this.$emit("remove-cycle", cycleId);
      await axios.delete(API_URL + "/specification/" + this.cycleId);
    },
    addReview: async function (cycleId) {
      await axios.patch(
        API_URL + "/specification/" + this.cycleId + "/Reviews",
        {
          Reviews: this.Reviews,
        }
      );
      this.$emit("review-added", cycleId);
    },
  },
};
</script>

<style scoped>
.row {
  display: flex;
  flex-wrap: wrap;
  padding: 0 4px;
}

#photo {
  height: 220px;
}

.btn {
  margin: 2.5px;
  border-width: 2px;
}
</style>