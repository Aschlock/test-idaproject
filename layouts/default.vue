<template>
  <div>
    <Header/>
    <Nuxt/>
  </div>
</template>

<style>

* {
  margin: 0;
  padding: 0;
}

a {
  text-decoration: none;
}

body {
  font-family: Arial;
  background: #FCFCFC;
}

.mr-2 {
  margin-right: 16px;
}

.mr-3 {
  margin-right: 24px;
}

.mr-5 {
  margin-right: 54px;
}

.mr-13 {
  margin-right: 104px;
}

.bold {
  font-weight: bold;
}

.base-color-300 {
  color: #677B8F;
}

.button {
  padding: 12px;
  box-sizing: border-box;
  color: white;
  background: #4959FF;
  border-radius: 16px;
}

.button__icon {

}

.lh-0 {
  line-height: 0;
}

.d-flex {
  display: flex;
}

.wrapper {
  max-width: 1920px;
  margin: 0 auto;
  padding: 0 64px;
}

@media (max-width: 768px) {
  .button__icon {
    height: 20px;
    width: 20px;
  }

  .button {
    padding: 6px;
    border-radius: 8px;
  }

  .wrapper {
    padding: 0 !important;
  }
}

</style>
<script>

import Header from "../components/Header";

export default {
  components: {Header}
}
</script>
