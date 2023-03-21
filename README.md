<a name="readme-top"></a>

<!-- TABLE OF CONTENTS -->
<details>
<summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#project-introduction">Project Introduction</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
        <li><a href="#data-source">Data Source</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#data-preparation-and-loading">Data Preparation and Loading</a></li>
        <li><a href="#setting-up-front-end">Setting Up Front-End</a></li>
        <li><a href="#setting-up-back-end">Setting Up Back-End</a></li>
      </ul>
    </li>
    <li>
      <a href="#crud-for-front-end-and-back-end">CRUD for Front-End and Back-End</a>
      <ul>
        <li><a href="#front-end-crud-setup">Front-End CRUD Setup</a></li>
        <li><a href="#back-end-crud-setup">Back-End CRUD Setup</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#references">REFERENCES</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## Project Introduction

[![Product Name Screen Shot][project-screenshot]](https://assignment1-eicot)

The MOTO Land website is created for motorcycle enthusiasts to provide valuable information of various motorcycles. With so many different models and types of motorcycles available, it can be overwhelming for someone who is looking to purchase one. </br>
With the website that offers detailed and honest reviews of various motorcycles can help consumers make informed decisions about which model is right for them. Additionally, motorcycle enthusiasts often enjoy reading reviews to learn about the latest trends and features in the industry. </br>
The website can also be a great platform for connecting with like-minded individuals and building a community of motorcycle enthusiasts. By sharing your experiences and knowledge about different models, you can help others make informed decisions and foster a sense of camaraderie within the motorcycle community. </br>
Overall, creating this MOTO Land website for motorcycle reviews can be a rewarding and valuable endeavor for both the creator and the users who benefit from the information provided.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


### Built With

The technologies below are used to create the MOTO Land Web;
* [Vue.js][vuejs-url]
* [MongDB][mongodb-url]
* [Express.js][Expressjs-url]
* [Axios][Axios-url]
* [Bootstrap][Bootstrap-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>


### Data Source

* Motorcycle Specifications Dataset from 1894 to present day. This data set is available at [Kaggle(Motorcycle Specifications Dataset)](https://www.kaggle.com/datasets/emmanuelfwerr/motorcycle-technical-specifications-19702022).


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

<!-- Data Preparation and Loading -->
### Data Preparation and Loading

* Data downloaed from Kaggle.com are availabe in csv format and filtered to 20 samples for this project.
* The sample data is uploaded to MongoDB Compass to reflect in MongoDB. MongoDB Compass can be downloaded [here](https://www.mongodb.com/try/download/shell).
    

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Setting Up Front-End -->
### Setting Up Front-End

The front-end is mainly implemented by using Vuejs, JavaScript framework for building interactrive user interface. Axios, the JavaScript library is also used for making HTTP requests from a back-end server and HTML, CSS and Bootstrap are used to create responsive and attractive user interface designs. </br>

Following setups for reference:

#### Setup for Vue
```
npm install -g @vue/cli
```
```
vue create .
```

   * Create project in current directory? Y
   * Please pick a preset. Vue3
   * Pick the package manager to use when installing dependencies: Use yarn
   
##### Create a file named vue.config.js and paste in the following lines:
```
module.exports = {
  // options...
  devServer: {
    disableHostCheck: true
  }
    }
```

#### Installing Bootstrap
```
yarn add bootstrap
```
```
yarn add bootstrap-vue
```
```
yarn add vue3-bootstrap5
```
##### Following codes to be added in main.js under src folder
```
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap/dist/js/bootstrap.js";
import "bootstrap-vue/dist/bootstrap-vue.css";
```

#### Installing Axios
```
yarn add axios
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Setting Up Back-End -->
### Setting Up Back-End
The separate github repository is created to setup back-end server to connect to MongoDB server. </br>
Following setups for reference:
```
npm install express
```
```
npm install cors
```
```
npm install mongodb
```
##### Create a file named .env and paste in the following lines (to change usernamne and password accordingly):
```
MONGO_URI = mongodb+srv://<username>:<password>@cluster0.tgaopw0.mongodb.net
```
##### Following codes to be added in index.js
```
const express = require('express');
const cors = require('cors');
const mongodb = require('mongodb');
const ObjectId = require('mongodb').ObjectId;
const MongoClient = mongodb.MongoClient;
const dotenv = require('dotenv');
dotenv.config();

let app = express();
app.use(express.json());
app.use(cors());
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CRUD for Front-End and Back-End -->
## CRUD for Front-End and Back-End
CRUD stands for Create, Read, Update, and Delete, which are the basic functions required for managing data in a website or a server:
- Create: The create function enables users to add new data to server through webpage

- Read: The read function allows users to access and view data that has already been created.

- Update: The update function allows users to modify existing data.

- Delete: The delete function enables users to remove data from a server.

<!-- Front-End CRUD Setup -->
### Front-End CRUD Setup
  1. Create Data to Server from Front-End using axios.post
  ```sh
  methods: {
    processAdd: async function () {
        await axios.post(API_URL + "/specification", {
          Brand: this.Brand,
          CoolingSystem: this.CoolingSystem,
          ColorOptions: this.ColorOptions.split(","), //to add string into array
        });
    },
  }
  ```
  2. Read Data from Server at Front-End using axios.get
  ```sh
  mounted: async function () {
    let response = await axios.get(API_URL + "/specification/" + this.cycleId);
    this.allCycles = response.data;
    this.Brand = response.data.Brand;
  }
  ```
  3. Update Data to Server through Front-End using axios.patch
  ```sh
 methods: {
    processUpdate: async function (cycleId) {
      await axios.patch(API_URL + "/specification/" + this.cycleId, {
        Brand: this.Brand,
        Model: this.Model,
        ColorOptions: this.ColorOptions.split(","), //to update string to array
      });
    },
  }
  ```
   4. Delete Data from Server using axios.delete
  ```sh
 methods: {
    remove: async function (cycleId) {
      this.$emit("remove-cycle", cycleId);
      await axios.delete(API_URL + "/specification/" + this.cycleId);
    }
    }
  ```
  
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Back-End CRUD Setup -->
### Back-End CRUD Setup
#### Connecting to MongoDB server
```sh
  async function connect() {
  const mongo_url = process.env.MONGO_URI;
  let client = await MongoClient.connect(mongo_url, {
    "useUnifiedTopology": true
  })
  let db = client.db("motorcycle");
  console.log("database connected");
  return db;
}
  ```

  1. Create Data to MongoDB using app.post
  ```sh
  app.post('/specification', async (req, res) => {
    let items = await db.collection('specification').insertOne({
      Brand: req.body.Brand,
      Engine: {//to create new objects dataset 
        Bore_mm: req.body.Bore,
        CoolingSystem: req.body.CoolingSystem}
    })
    res.json(items);
  })
  ```
  2. Read Data from MongoDB using app.patch
  ```sh
  app.get('/specification', async (req, res) => {
    let items = await db.collection('specification').find().toArray();
    res.json(items)

  })
  ```
  3. Update particualr Data to MongoDB using app.patch
  ```sh
 app.patch('/specification/:id', async (req, res) => {
    let results = await db.collection('specification').updateOne({
      '_id': new ObjectId(req.params.id),
    }, {
      '$set': {
        Brand: req.body.Brand,
        'Engine.Bore_mm': req.body.Bore, //to update object data
        'Engine.CoolingSystem': req.body.CoolingSystem,
        '
      }
    })
    res.json({
      'status': true
    })
  })
  ```
   4. Delete Data from MongoDB using app.delete
  ```sh
 app.delete('/specification/:id', async (req, res) => {
    let results = await db.collection('specification').deleteOne({
      '_id': new ObjectId(req.params.id)
    })
    res.json({
      'message': 'Success'
    })
  })
  ```
  
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- USAGE EXAMPLES -->
## Usage
  [Web Page Link](https://assignment1-eicot.eicot.repl.co)
  ![screenshot](images/screenshot.png)
  In this view, the base layers are divided into default view, terrain view and night view, and it is displayed at right top of the map. Search button is placed on the left top and can be used to search Sub Zones name in Singapore. It will direct to the location and zoom it in the center of the map. 
  
  ![screenshot](images/screenshot1.png)
In this plot view, overlay layers are shown as below:

  * Overall Resident Population
  * Female Resident Population
  * Male Resident Population
  * Resident Population Aged Below 5 Years
  * Resident Population Aged 65 Years and Over
  * Resident Population Staying in HDB Flats
  * Resident Population Staying in Condominium
  * Resident Population Staying in Landed Properties

Lastly, the markers layer for sub zones is added to location the center of the zones. By viewing the above layers, user will be able to clearly identify the most populated area and the least area based on gender, ages and type of residence. Additionally, the Legend on the right bottom will state the number of people staing in sub zones based on coloring.

There are also three sections to choose Chart options on right top of web page:

  1. Population (1960 - 2021): It provides tracking information of total population, female/male population and population ages 0-14, 15-64 and 65+ from 1960 to 2021
  2. Population Rate (1960 - 2021): Similarly, it shows annual population growth and trend of birth rate, fertility rate and death rate
  3. Overview: It illustrates clear view of recent overall population and annual growth rate showing constant growth from 2012 to 2020 and declined in 2021.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- REFERENCES -->
## REFERENCES

* Provides Animated Marker Clustering functionality for Leaflet, a JS library for interactive maps.The file is available at [Leaflet Marker Cluster](https://github.com/Leaflet/Leaflet.markercluster)
* A Leaflet control that search markers/features location by custom property. The file is available at [Leaflet Search Control](https://opengeo.tech/maps/leaflet-search/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- IMAGES & URLS -->

[project-screenshot]: images/population1.jpg
[geojsonio]: images/geojsonio.png
[vuejs-url]: https://vuejs.org
[mongodb-url]: https://www.mongodb.com
[Axios-url]: https://axios-http.com
[Bootstrap-url]:https://getbootstrap.com
[Expressjs-url]: https://expressjs.com



