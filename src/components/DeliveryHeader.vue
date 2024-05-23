<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'DeliveryHeader'
})
</script>
<template>
  <div class="delivery__header">
    <div class="delivery__header-logo">
      <img src="@/img/logo.svg" alt="logo" />
      <h2>FastService</h2>
    </div>
    <div class="delivery__header-text">
      <h1>Delivery cost</h1>
      <p>Enter name of the city to count delivery cost</p>
    </div>
  </div>
</template>
