<script setup lang="ts">
  import Base from './components/Base.vue'
  import Error from './components/Error.vue'
  import { useDisplay } from 'vuetify'
  
  const { smAndDown } = useDisplay()

</script>

<template>
    <Base v-if="smAndDown == false" />
    <Error v-else />
</template>

<style scoped>
</style>
