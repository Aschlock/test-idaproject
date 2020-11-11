<template>
  <div class="wrapper">
    <div class="main-block">
      <div class="main-block__controllers">
        <div class="main-block__selector">
          Rent <span class="main-color-400">whatever</span>
          <span>
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 16L6 9.99965L8.00094 8L12 12.0007L15.9991 8L18 9.99965L12 16Z" fill="#4959FF"/>
          </svg>
        </span>
        </div>

        <div class="main-block__add main-color-400 d-flex">
          <div class="add__text">
            Add new
          </div>
          <div class="button lh-0">
            <svg class="button__icon" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M11 11V5H13V11H19V13H13V19H11V13H5V11H11Z" fill="#FCFCFC"/>
            </svg>
          </div>
        </div>
      </div>
      <div class="vehicle-list">
        <vehicle-block v-bind:vehicle="vehicle"
                       v-for="vehicle in vehicles"
                       @click.prevent="openVehicle(vehicle)"/>
      </div>
    </div>
  </div>
</template>

<script>
import {getVehicles} from "../middleware/request";
import VehicleBlock from "./VehicleBlock";

export default {
  methods: {
    openVehicle(vehicle) {
      this.$router.push('/vehicles/' + vehicle.id)
    }
  },
  middleware: 'request',
  data: () => {
    return {
      vehicles: []
    }
  },
  beforeMount() {

  },
  async fetch() {
    this.vehicles = await getVehicles();
  },
  mounted() {

  },
  name: "Vehicles",
  components: {VehicleBlock}
}
</script>

<style scoped>

.wrapper {
  max-width: 1920px;
  margin: 0 auto;

  max-width: 1920px;
  margin: 0 auto;
  padding: 0 64px;
}

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

.vehicle__link {
  text-decoration: none;
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
  }

}

@media (max-width: 525px) {
  .vehicle-list {
    margin: 0;
  }
}

</style>
