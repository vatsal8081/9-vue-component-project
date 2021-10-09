<template>
  <p> ----------  From Demo Prop   ---------------------</p>
  <div v-for="item in friends" :key="item">
      <p> {{ item }} </p>
  </div>  
</template>

<script>
export default {

    props: {
        friends: {
            type: Array,
            require: true
        }
    }

}
</script>

<style>

</style>