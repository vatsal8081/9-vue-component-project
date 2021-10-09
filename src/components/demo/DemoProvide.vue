<template>
    <p> ----------  From Demo Provide   ---------------------</p>
  <div v-for="item in friends" :key="item">
      <p> {{ item }} </p>
  </div>

</template>

<script>
export default {
    inject: ['friends']
}
</script>

<style>

</style>