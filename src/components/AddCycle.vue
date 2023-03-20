<template>
  <div>
    <div class="row">
      <h1 class="pt-3 text-center">Add New Motorcycle</h1>
      <div class="col-1"></div>
      <div class="col-9">
        <form v-on:submit.prevent="processAdd">
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Brand: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Brand" />
              <div class="notiAlert" v-if="showAlert">{{ BrandAlert }}</div>
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Model: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Model" />
              <div class="notiAlert" v-if="showAlert">
                {{ ModelAlert }}
              </div>
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Type: </label>
            <div class="col-sm-9">
              <select class="form-select" v-model="Category">
                <option value="Classic">Classic</option>
                <option value="Enduro / offroad">Enduro / offroad</option>
                <option value="Naked bike">Naked Bike</option>
                <option value="Scooter">Scooter</option>
                <option value="Sport">Sport</option>
                <option value="Touring">Touring</option>
              </select>
              <div class="notiAlert" v-if="showAlert">
                {{ CategoryAlert }}
              </div>
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Year: </label>
            <div class="col-sm-9">
              <select class="form-select" v-model="Year">
                <option value="2022">2022</option>
                <option value="2021">2021</option>
                <option value="2020">2020</option>
                <option value="2019">2019</option>
                <option value="2018">2018</option>
                <option value="2017">2017</option>
              </select>
              <div class="notiAlert" v-if="showAlert">{{ YearAlert }}</div>
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Image(URL): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Image" />
              <div class="notiAlert" v-if="showAlert">{{ ImageAlert }}</div>
            </div>
          </div>
          <div class="row mb-3 form-group">
            <label class="col-sm-3 col-form-label">Description: </label>
            <div class="col-sm-9">
              <textarea
                type="text"
                class="form-control"
                v-model="Description"
                rows="4"
              ></textarea>
              <div class="notiAlert" v-if="showAlert">
                {{ DescriptionAlert }}
              </div>
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Colors Available: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="ColorOptions" />
            </div>
          </div>
          <div class="row mb-3">
            <h5>Engine and Transmission Specifications</h5>
            <label class="col-sm-3 col-form-label">Bore(mm): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Bore" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Cooling System: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="CoolingSystem" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Cylinder: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Cylinder" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-4 col-form-label">Displacement(ccm): </label>
            <div class="col-sm-8">
              <input type="text" class="form-control" v-model="Displacement" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Gearbox: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Gearbox" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Power(hp): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Power" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Stroke: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Stroke" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Torque(Nm): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Torque" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Transmission: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Transmission" />
            </div>
          </div>
          <div class="row mb-3">
            <h5>Fuel System</h5>
            <label class="col-sm-3 col-form-label">Capacity(lts): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Capacity" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Control: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Control" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">System: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="System" />
            </div>
          </div>
          <div class="row mb-3">
            <h5>Dimensions and Brake System</h5>
            <label class="col-sm-3 col-form-label">Weight(kg): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Weight" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Seat Height(mm): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="SeatHeight" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">Wheelbase(mm): </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="Wheelbase" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">FrontBrakes: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="FrontBrakes" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">FrontSuspension: </label>
            <div class="col-sm-9">
              <input
                type="text"
                class="form-control"
                v-model="FrontSuspension"
              />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">FrontTire: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="FrontTire" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">RearBrakes: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="RearBrakes" />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">RearSuspension: </label>
            <div class="col-sm-9">
              <input
                type="text"
                class="form-control"
                v-model="RearSuspension"
              />
            </div>
          </div>
          <div class="row mb-3">
            <label class="col-sm-3 col-form-label">RearTire: </label>
            <div class="col-sm-9">
              <input type="text" class="form-control" v-model="RearTire" />
            </div>
          </div>
          <div></div>
        </form>
        <button
          class="btn btn-outline-dark col-12 text-center"
          v-on:click="processAdd"
          type="button"
        >
          <h3>Submit</h3>
        </button>
      </div>
      <div class="col-1"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API_URL = "https://assignment2.eicot.repl.co";
export default {
  name: "AddCycle",
  data: function () {
    return {
      Brand: "",
      BrandAlert: "Brand is required*",
      Model: "",
      ModelAlert: "Model is required*",
      Year: "",
      YearAlert: "Manufacture Year is required*",
      Image: "",
      ImageAlert: "Image(URL) is required*",
      Description: "",
      DescriptionAlert: "Description is required*",
      Category: "",
      CategoryAlert: "Type is required*",
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
      errors: [],
      showAlert: false,
    };
  },

  methods: {
    processAdd: async function (e) {
      if (!this.Brand) {
        this.showAlert = true;
        return;
      } else if (!this.Model) {
        this.showAlert = true;
        return;
      }
      if (!this.Category) {
        this.showAlert = true;
        return;
      }
      if (!this.Year) {
        this.showAlert = true;
        return;
      }
      if (!this.Image) {
        this.showAlert = true;
        return;
      }
      if (!this.Description) {
        this.showAlert = true;
        return;
      } else
        await axios.post(API_URL + "/specification", {
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
      this.$emit("cycle-added");
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

.notiAlert {
  color: red;
}
</style>