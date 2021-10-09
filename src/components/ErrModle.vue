<template>
  <dialog open>
      <slot></slot>
      <button @click="$emit('ok-click')">OK</button>
      </dialog>        
</template>

<script>
export default {

    emits: ['ok-click']

}
</script>

<style>

</style>