<script setup lang="ts">
  import Base from './components/Base.vue'
  import Error from './components/Error.vue'
  import { useDisplay } from 'vuetify'

  const { mobile } = useDisplay()
</script>

<template>
    <Base v-if="mobile == false" />
    <Error v-else />
</template>

<style scoped>
</style>
