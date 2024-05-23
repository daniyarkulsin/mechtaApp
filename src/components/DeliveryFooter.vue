<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'delivery-footer'
})
</script>
<template lang="">
  <footer class="delivery__footer">
    <h5>All rights reserved Fast service 2021</h5>
    <div>
      <img src="@/img/visa.svg" alt="visa" />
      <img src="@/img/masterCard.svg" alt="master card" />
      <img src="@/img/maestro.svg" alt="maestro" />
      <img src="@/img/processing.png" alt="processing" />
    </div>
  </footer>
</template>
