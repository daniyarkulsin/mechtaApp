<script lang="ts">
import { defineComponent } from 'vue'
interface State {
  selectedOption: String
}
export default defineComponent({
  props: {
    complitedCityArr: {
      type: Object,
      required: true
    }
  },
  data(): State {
    return {
      selectedOption: ''
    }
  }
})
</script>

<template>
  <form class="delivery__order-form">
    <label
      v-for="(order, index) in complitedCityArr"
      :class="{ active: order.type === selectedOption, opacity: !order.available }"
      :key="index"
      class="delivery__order-label"
    >
      <div class="delivery__order-inner">
        <input v-model="selectedOption" name="drone" type="radio" :value="order.type" />
        <h2>{{ order.type[0].toUpperCase() + order.type.slice(1) }}</h2>
        <h3>{{ order.price }}$</h3>
      </div>
      <img :src="`src/img/${order.type}.svg`" alt="#" />
    </label>
  </form>
</template>
