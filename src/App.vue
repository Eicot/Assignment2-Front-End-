<template>
  <div class="home">
    <div>
      <nav class="navbar navbar-expand-md body-tertiary">
        <div class="container-fluid">
          <a class="navbar-brand" href="toMain">Cycle Review </a>
          <button
            class="navbar-toggler justify-content-end"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#mainbar"
            aria-controls="mainbar"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div
            class="collapse navbar-collapse justify-content-end"
            id="mainbar"
          >
            <ul class="nav nav-tabs">
              <li class="nav-item">
                <button
                  class="nav-link active"
                  v-on:click="toMain"
                  type="button"
                  data-bs-toggle="tab"
                >
                  Home
                </button>
              </li>
              <li class="nav-item">
                <button
                  class="nav-link"
                  v-on:click="toAddNew"
                  type="button"
                  data-bs-toggle="tab"
                >
                  Add New <font-awesome-icon icon="fa-solid fa-motorcycle" />
                  <i class="fa-solid fa-motorcycle"></i>
                </button>
              </li>
              <li class="nav-item">
                <button
                  class="nav-link"
                  v-on:click="toAboutUs"
                  type="button"
                  data-bs-toggle="tab"
                >
                  About us
                </button>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </div>

    <div>
      <div class="alert alert-succcess notification" v-if="showAlert">
        {{ alertMessage }}
      </div>
      <main>
        <Home v-if="page == 'mainPage'" v-on:view-cycle="toSpec" />
      </main>
      <AddCycle v-if="page == 'addNewPage'" v-on:cycle-added="cycleAdded" />
      <Specification
        v-if="page == 'specPage'"
        v-bind:cycleId="viewSpec"
        v-on:edit-cycle="toEdit"
        v-on:remove-cycle="deleteCycle"
        v-on:review-added="reviewAdded"
      />
      <EditCycle
        v-if="page == 'editPage'"
        v-bind:cycleId="editSpec"
        v-on:cycle-updated="cycleUpdated"
      />
      <Aboutus v-if="page == 'aboutUs'" />
    </div>
  </div>
</template>

<script>
import Home from "./components/Home";
import AddCycle from "./components/AddCycle";
import Specification from "./components/Specification";
import EditCycle from "./components/EditCycle";
import Aboutus from "./components/Aboutus";

export default {
  name: "App",
  components: {
    Home,
    AddCycle,
    Specification,
    EditCycle,
    Aboutus,
  },
  data: function () {
    return {
      page: "mainPage",
      viewSpec: 0,
      editSpec: 0,
      alertMessage: "",
      showAlert: false,
    };
  },
  methods: {
    toMain: function () {
      this.page = "mainPage";
      this.showAlert = false;
    },
    toAddNew: function () {
      this.page = "addNewPage";
      this.showAlert = false;
    },
    cycleAdded: function () {
      this.page = "mainPage";
      this.alertMessage = "A new cycle has been added";
      this.showAlert = true;
      setTimeout(() => {
        this.showAlert = false;
      }, 2000);
    },
    toSpec: function (cycleId) {
      this.page = "specPage";
      this.viewSpec = cycleId;
      this.showAlert = false;
    },
    toEdit: function (cycleId) {
      this.page = "editPage";
      this.editSpec = cycleId;
      this.showAlert = false;
    },
    cycleUpdated: function (cycleId) {
      this.page = "specPage";
      this.alertMessage = "The cycle has been updated";
      this.showAlert = true;
      setTimeout(() => {
        this.showAlert = false;
      }, 2000);
    },
    deleteCycle: function () {
      this.page = "mainPage";
      this.alertMessage = "The cycle has been deleted";
      this.showAlert = true;
      setTimeout(() => {
        this.showAlert = false;
      }, 2000);
    },
    reviewAdded: function (cycleId) {
      this.page = "specPage";
      this.alertMessage = "A review has been added";
      this.showAlert = true;
      setTimeout(() => {
        this.showAlert = false;
      }, 2000);
    },
    toAboutUs: function () {
      this.page = "aboutUs";
      this.showAlert = false;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.cdnfonts.com/css/motorcycle");
.home {
  background-image: url(https://c4.wallpaperflare.com/wallpaper/612/547/823/wall-brick-texture-units-wallpaper-preview.jpg);
  font-family: Rockwell;
  font-size: 20px;
}
main {
  margin-left: 3rem;
  margin-right: 3rem;
  padding: 2rem;
}

.notification {
  background-color: #000000;
  color: white;
  padding: 16px;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translateX(-50%);
  z-index: 9999;
}

.nav-link {
  color: rgb(0, 0, 0);
}
</style>
