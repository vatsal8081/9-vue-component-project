<template>
  <div v-for="(resource, i) in resources" :key="i">
      <p>Title: {{ resource.title }}</p> 
      <p>Description: {{ resource.description }}</p> 
      <a :href="resource.link">Go To</a>
      <button @click="$emit('delete-resource', i)">Delete</button>
  </div>
</template>

<script>
export default {
    props: {
        resources: {
            type: Object,
            require: true
        }
    },
    $emits: ['delete-resource']
    

}
</script>

<style>

</style>