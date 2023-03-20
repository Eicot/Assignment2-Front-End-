<template>
  <div>
    <div class="row">
      <div class="col-1"></div>
      <div class="col-10">
        <div class="row">
          <img class="col-5" v-bind:src="allCycles.Image" id="photo" />
          <div class="col-7">
            <textarea
              type="text"
              class="form-control"
              v-model="Description"
              rows="9"
            ></textarea>
          </div>
        </div>
        <div class="row">
          <div class="col-12">
            <h1>{{ Brand }} {{ Model }}</h1>
          </div>
        </div>
        <div class="row"></div>
        <table class="action_table">
          <tbody>
            <tr class="blank_row">
              <td colspan="3">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2">
                <h5>General Information</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td class="col-4">Brand:</td>
              <td>
                <input type="text" class="form-control col-8" v-model="Brand" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Model:</td>
              <td>
                <input type="text" class="form-control" v-model="Model" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Type:</td>
              <td>
                <select class="form-select" v-model="Category">
                  <option value="Classic">Classic</option>
                  <option value="Enduro / offroad">Enduro / offroad</option>
                  <option value="Naked bike">Naked Bike</option>
                  <option value="Scooter">Scooter</option>
                  <option value="Sport">Sport</option>
                  <option value="Touring">Touring</option>
                </select>
              </td>
            </tr>
            <tr class="data_row">
              <td>Year:</td>
              <td>
                <select class="form-select" v-model="Year">
                  <option value="2022">2022</option>
                  <option value="2021">2021</option>
                  <option value="2020">2020</option>
                  <option value="2019">2019</option>
                  <option value="2018">2018</option>
                  <option value="2017">2017</option>
                </select>
              </td>
            </tr>
            <tr class="data_row">
              <td>Colors Available:</td>
              <td>
                <input
                  type="text"
                  class="form-control"
                  v-model="ColorOptions"
                />
              </td>
            </tr>
            <tr class="data_row">
              <td>Image(URL):</td>
              <td>
                <textarea
                  type="text"
                  class="form-control"
                  v-model="Image"
                  rows="3"
                ></textarea>
              </td>
            </tr>

            <tr class="blank_row">
              <td colspan="3">&nbsp;</td>
            </tr>

            <tr class="header_row">
              <td colspan="2">
                <h5>Engine and Transmission Specifications</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td>Bore(mm):</td>
              <td>
                <input type="text" class="form-control" v-model="Bore" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Cooling System:</td>
              <td>
                <input
                  type="text"
                  class="form-control"
                  v-model="CoolingSystem"
                />
              </td>
            </tr>
            <tr class="data_row">
              <td>Cylinder:</td>
              <td>
                <input type="text" class="form-control" v-model="Cylinder" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Displacement(ccm):</td>
              <td>
                <input
                  type="text"
                  class="form-control"
                  v-model="Displacement"
                />
              </td>
            </tr>
            <tr class="data_row">
              <td>Gearbox:</td>
              <td>
                <input type="text" class="form-control" v-model="Gearbox" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Power(hp):</td>
              <td>
                <input type="text" class="form-control" v-model="Power" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Stroke:</td>
              <td>
                <input type="text" class="form-control" v-model="Stroke" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Torque(Nm):</td>
              <td>
                <input type="text" class="form-control" v-model="Torque" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Transmission Type:</td>
              <td>
                <input
                  type="text"
                  class="form-control"
                  v-model="Transmission"
                />
              </td>
            </tr>

            <tr class="blank_row">
              <td colspan="3">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2">
                <h5>Fuel System</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td>Fuel Capacity(lts):</td>
              <td>
                <input type="text" class="form-control" v-model="Capacity" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Fuel Control:</td>
              <td>
                <input type="text" class="form-control" v-model="Control" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Fuel System:</td>
              <td>
                <input type="text" class="form-control" v-model="System" />
              </td>
            </tr>

            <tr class="blank_row">
              <td colspan="3">&nbsp;</td>
            </tr>
            <tr class="header_row">
              <td colspan="2">
                <h5>Dimension and Brake System</h5>
              </td>
            </tr>
            <tr class="data_row">
              <td>Weight(kg):</td>
              <td>
                <input type="text" class="form-control" v-model="Weight" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Seat Height(mm):</td>
              <td>
                <input type="text" class="form-control" v-model="SeatHeight" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Wheelbase(mm):</td>
              <td>
                <input type="text" class="form-control" v-model="Wheelbase" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Front Brakes:</td>
              <td>
                <input type="text" class="form-control" v-model="FrontBrakes" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Rear Brakes:</td>
              <td>
                <input type="text" class="form-control" v-model="RearBrakes" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Front Suspension:</td>
              <td>
                <input
                  type="text"
                  class="form-control"
                  v-model="FrontSuspension"
                />
              </td>
            </tr>
            <tr class="data_row">
              <td>Rear Suspension:</td>
              <td>
                <input
                  type="text"
                  class="form-control"
                  v-model="RearSuspension"
                />
              </td>
            </tr>
            <tr class="data_row">
              <td>Front Tire:</td>
              <td>
                <input type="text" class="form-control" v-model="FrontTire" />
              </td>
            </tr>
            <tr class="data_row">
              <td>Rear Tire:</td>
              <td>
                <input type="text" class="form-control" v-model="RearTire" />
              </td>
            </tr>
          </tbody>
          <tr class="blank_row">
            <td colspan="3">&nbsp;</td>
          </tr>
        </table>
        <button
          class="btn btn-outline-dark col-12 text-center"
          v-on:click="processUpdate(cycleId)"
        >
          <h3>Update</h3>
        </button>
        <tr class="blank_row">
          <td colspan="3">&nbsp;</td>
        </tr>
      </div>
      <div class="col-1"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API_URL = "https://assignment2.eicot.repl.co";
export default {
  name: "EditCycle",
  data: function () {
    return {
      allCycles: "",
      Brand: "",
      Model: "",
      Year: "",
      Image: "",
      Description: "",
      Category: "",
      Bore: "",
      CoolingSystem: "",
      Cylinder: "",
      Displacement: "",
      Gearbox: "",
      Power: "",
      Stroke: "",
      Torque: "",
      Transmission: "",
      Capacity: "",
      Control: "",
      System: "",
      Weight: "",
      SeatHeight: "",
      Wheelbase: "",
      FrontBrakes: "",
      FrontSuspension: "",
      FrontTire: "",
      RearBrakes: "",
      RearSuspension: "",
      RearTire: "",
      ColorOptions: "",
    };
  },
  props: ["cycleId"], //receive cycleId information from App.vue
  mounted: async function () {
    let response = await axios.get(API_URL + "/specification/" + this.cycleId);
    this.allCycles = response.data;
    this.Brand = response.data.Brand;
    this.Model = response.data.Model;
    this.Year = response.data.Year;
    this.Image = response.data.Image;
    this.Description = response.data.Description;
    this.Category = response.data.Category;
    this.Bore = response.data.Engine.Bore_mm;
    this.CoolingSystem = response.data.Engine.CoolingSystem;
    this.Cylinder = response.data.Engine.Cylinder;
    this.Displacement = response.data.Engine.Displacement_ccm;
    this.Gearbox = response.data.Engine.Gearbox;
    this.Power = response.data.Engine.Power_hp;
    this.Stroke = response.data.Engine.Stroke;
    this.Torque = response.data.Engine.Torque_Nm;
    this.Transmission = response.data.Engine.TransmissionType;
    this.Capacity = response.data.Fuel.Capacity_lts;
    this.Control = response.data.Fuel.Control;
    this.System = response.data.Fuel.System;
    this.Weight = response.data.Physical.DryWeight_kg;
    this.SeatHeight = response.data.Physical.SeatHeight_mm;
    this.Wheelbase = response.data.Physical.Wheelbase_mm;
    this.FrontBrakes = response.data.Wheel.FrontBrakes;
    this.FrontSuspension = response.data.Wheel.FrontSuspension;
    this.FrontTire = response.data.Wheel.FrontTire;
    this.RearBrakes = response.data.Wheel.RearBrakes;
    this.RearSuspension = response.data.Wheel.RearSuspension;
    this.RearTire = response.data.Wheel.RearTire;
    this.ColorOptions = response.data.ColorOptions.join(", ");
  },
  methods: {
    processUpdate: async function (cycleId) {
      await axios.patch(API_URL + "/specification/" + this.cycleId, {
        Brand: this.Brand,
        Model: this.Model,
        Year: this.Year,
        Image: this.Image,
        Description: this.Description,
        Category: this.Category,
        Bore: this.Bore,
        CoolingSystem: this.CoolingSystem,
        Cylinder: this.Cylinder,
        Displacement: this.Displacement,
        Gearbox: this.Gearbox,
        Power: this.Power,
        Stroke: this.Stroke,
        Torque: this.Torque,
        Transmission: this.Transmission,
        Capacity: this.Capacity,
        Control: this.Control,
        System: this.System,
        Weight: this.Weight,
        SeatHeight: this.SeatHeight,
        Wheelbase: this.Wheelbase,
        FrontBrakes: this.FrontBrakes,
        FrontSuspension: this.FrontSuspension,
        FrontTire: this.FrontTire,
        RearBrakes: this.RearBrakes,
        RearSuspension: this.RearSuspension,
        RearTire: this.RearTire,
        ColorOptions: this.ColorOptions.split(","),
      });
      this.$emit("cycle-updated", cycleId);
    },
  },
};
</script>

<style scoped>
.textarea {
  width: 100%;
  height: 200px;
  resize: none;
}
input {
  width: 100%;
  text-decoration: none;
  margin: 4px 2px;
}
.btn-outline-dark {
  border-width: 4px;
}
</style>