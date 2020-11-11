<template>
  <div class="vehicle">
    <img :src="vehicle.preview" class="vehicle__image" width="88" height="88" alt=""/>
    <div class="vehicle__text">
      <div class="vehicle__name">
        {{ vehicle.name }}
      </div>
      <div class="vehicle__desc">
        {{ vehicle.description }}
      </div>
      <div class="vehicle__price">
        {{vehicle.rent}} $/h
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VehicleBlock",
  props: ['vehicle']
}
</script>

<style scoped>
.vehicle {
  background: #FCFCFC;
  border-radius: 32px;
  margin: 16px;
  padding: 24px 32px;
  display: flex;
  width: 100%;
  /*max-width: 373.33px;*/
  /*min-width: 343px;*/
  flex: 1 1 30%;
  height: 164px;
  box-sizing: border-box;
}

.vehicle__image {
  border-radius: 24px;
  margin-right: 24px;
}

.vehicle__text {
  text-decoration: none;
  padding: 16px 0 0;
}

.vehicle__name {
  font-weight: bold;
  font-size: 16px;
  line-height: 14px;
  color: #012345;
  margin-bottom: 12px;
}

.vehicle__desc {
  font-weight: 300;
  font-size: 12px;
  line-height: 148%;
  color: #677B8F;
  margin-bottom: 16px;
}

.vehicle__price {
  font-weight: bold;
  font-size: 14px;
  line-height: 148%;
  color: #F84AB3;
}

@media (max-width: 768px) {
  .vehicle {
    margin: 0 16px 12px;
    padding: 20px;
  }

  .vehicle__image {
    border-radius: 16px;
    margin-right: 20px;
  }

  .vehicle__text {
    padding: 8px 0 0;
  }
}

@media (max-width: 525px) {
  .vehicle {
    margin: 0 0 16px;
  }
}
</style>
