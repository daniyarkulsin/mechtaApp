<script lang="ts">
import DeliveryForm from '@/components/DeliveryForm.vue'
import DeliveryCityList from '@/components/DeliveryCityList.vue'
import DeliveryFooter from '@/components/DeliveryFooter.vue'
import DeliveryOrder from '@/components/DeliveryOrder.vue'
import DeliveryCarContent from '@/components/DeliveryCarContent.vue'
import DeliveryHeader from '@/components/DeliveryHeader.vue'
const URL = 'https://frontend-test.dev.mechta.kz/delivery/check'

import { defineComponent } from 'vue'

interface State {
  availableCitys: String[]
  complitedCityArr: {
    city: String
    type: String
    available: Boolean
    price: Number
  }[]
  loading: Boolean
  cityInputError: Boolean
}
export default defineComponent({
  components: {
    DeliveryCarContent,
    DeliveryForm,
    DeliveryCityList,
    DeliveryFooter,
    DeliveryOrder,
    DeliveryHeader
  },
  data(): State {
    return {
      availableCitys: ['almaty', 'nur-sultan', 'aktau'],
      complitedCityArr: [],
      loading: false,
      cityInputError: false
    }
  },
  methods: {
    addCity(text: string) {
      const newText = text.trim().toLocaleLowerCase()
      if (this.availableCitys.find((city) => newText === city)) {
        this.getData(newText)
        this.cityInputError = false
      } else {
        this.cityInputError = true
      }
    },
    async getData(text: string) {
      try {
        const response = await fetch(`${URL}?search=${encodeURIComponent(text)}`)
        if (!response.ok) {
          throw new Error('Network response was not ok')
        }
        const data = await response.json()
        console.log(data)
        this.complitedCityArr = data
      } catch (error) {
        console.error(error)
      }
    },
    toggleCityInputError() {
      this.cityInputError = false
      this.complitedCityArr = []
    },
    resetRadioBtn() {}
  }
})
</script>

<template>
  <div class="delivery__container">
    <div class="delivery__content-left">
      <DeliveryHeader />
      <DeliveryForm
        @submit-form="addCity"
        @clear-form="toggleCityInputError"
        :cityInputError="cityInputError"
        :complitedCityArr="complitedCityArr"
      />
      <DeliveryCityList />
      <DeliveryFooter />
    </div>

    <div class="delivery__content-right">
      <DeliveryOrder
        v-if="!cityInputError && complitedCityArr.length != 0"
        :complitedCityArr="complitedCityArr"
      />
      <DeliveryCarContent v-else />
    </div>
  </div>
</template>
