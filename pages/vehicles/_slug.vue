<template>
<div class="wrapper">
  {{vehicle}}

  <p style="color: red">{{$route.params.slug}}</p>
</div>
</template>

<script>
export default {
  props: ['vehicle'],
}
</script>

<style scoped>

</style>
