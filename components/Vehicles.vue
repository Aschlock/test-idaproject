<template>
  <div class="wrapper">
    <div class="main-block">
      <div class="main-block__controllers">
        <div class="main-block__selector">
          Rent
          <span class="select-wrapper">
            <select class="main-block__selector main-block__select main-color-400"
                    v-model="selected"
                    v-on:change="filterVehicles">
                <option>whatever</option>
              <option v-for="type in types">{{ type }}</option>

            </select>
          </span>
          <span>
        </span>
        </div>

        <div class="main-block__add main-color-400 d-flex">
          <div class="add__text">
            Add new
          </div>
          <div class="button lh-0">
            <svg class="button__icon" width="24" height="24" viewBox="0 0 24 24" fill="none"
                 xmlns="http://www.w3.org/2000/svg">
              <path d="M11 11V5H13V11H19V13H13V19H11V13H5V11H11Z" fill="#FCFCFC"/>
            </svg>
          </div>
        </div>
      </div>
      <div class="vehicle-list">
        <vehicle-block v-bind:vehicle="vehicle"
                       v-for="vehicle in vehicles"
        />
      </div>
    </div>
  </div>
</template>

<script>
import {getVehicles} from "../middleware/request";
import VehicleBlock from "./VehicleBlock";

export default {
  middleware: 'request',
  // async fetch({store}) {
  //   if (store.getters['vehicles/vehicles'].length === 0) {
  //     await store.dispatch('vehicles/fetch')
  //   }
  // },
  data: () => {
    return {
      vehicles: [],
      filteredVehicles: [],
      types: [],
      selected: 'whatever'
    }
  },
  async fetch() {
    this.vehicles = await getVehicles();
    this.filteredVehicles = this.vehicles
  },


  methods: {
    filterVehicles() {
      if (this.selected === 'whatever') {
        this.filteredVehicles = this.vehicles
      } else {
        this.filteredVehicles = this.vehicles.filter(a => {
          return a.type === this.selected
        })
      }
    }
  },
  beforeMount() {

  },
  mounted() {
    let types = new Set()
    for (let i = 0; i < this.vehicles.length; ++i) {
      types.add(this.vehicles[i].type)
    }

    this.types = types
    console.log(types)
  },
  name: "Vehicles",
  components: {VehicleBlock}
}
</script>

<style scoped>


.main-block {
  background: #F3F4F7;
  border-radius: 48px;
  padding: 56px 64px;
}

.main-block__controllers {
  margin-bottom: 40px;
  display: flex;
  justify-content: space-between;
}

.main-block__selector {
  font-weight: bold;
  font-size: 40px;
  line-height: 120%;
}

.main-block__select {
  border: none;
  -moz-appearance: none; /* Firefox */
  -webkit-appearance: none; /* Safari and Chrome */
  appearance: none;
  outline: none;
  cursor: pointer;
  background: url("~@/assets/arrow.svg") no-repeat right center;
  padding-right: 40px;
  overflow: visible;
}

option {
  font-size: 14px;
}

.main-block__add {
  font-weight: bold;
  font-size: 20px;
  line-height: 140%;
  display: flex;
  align-items: center;
}

.add__text {
  margin-right: 20px;
}

.main-color-400 {
  color: #4959FF;
}

.vehicle-list {
  display: flex;
  justify-content: space-between;

  flex-wrap: wrap;
  margin: -16px;
  box-sizing: border-box;
}

@media (max-width: 768px) {
  .main-block {
    padding: 26px 16px;
    border-radius: 24px;
  }

  .main-block__selector {
    font-size: 24px;
  }

  .main-block__controllers {
    margin-bottom: 24px;
  }

  .add__text {
    font-size: 16px;
    margin-right: 12px;
  }

  .main-block__select {
    background-size: 16px;
    padding-right: 20px;
  }
}

@media (max-width: 525px) {
  .vehicle-list {
    margin: 0;
  }
}

</style>
