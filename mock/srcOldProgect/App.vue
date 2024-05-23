<script>
import DeliveryForm from '@/components/DeliveryForm.vue'
import DeliveryCityList from '@/components/DeliveryCityList.vue'
import DeliveryFooter from '@/components/DeliveryFooter.vue'
import DeliveryOrder from '@/components/DeliveryOrder.vue'
import DeliveryCarContent from '@/components/DeliveryCarContent.vue'
import DeliveryHeader from '@/components/DeliveryHeader.vue'
const URL = 'https://frontend-test.dev.mechta.kz/delivery/check'
import axios from 'axios'

export default {
  components: {
    DeliveryForm,
    DeliveryCityList,
    DeliveryFooter,
    DeliveryOrder,
    DeliveryCarContent,
    DeliveryHeader,
  },
  data() {
    return {
      service: false,
      citys: ['almaty', 'nur-sultan', 'aktau'],
      orderArray: [],
    }
  },
  methods: {
    async getData(text) {
      try {
        const response = await axios.get(URL, {
          params: {
            search: text,
          },
        })
        console.log(response.data)
        this.service = true
        this.orderArray = response.data
      } catch (error) {
        console.log(error)
        this.service = false
      }
    },
  },
}
</script>

<template>
  <div class="container">
    <div class="delivery__content">
      <DeliveryHeader />
      <DeliveryForm
        :service="service"
        :citys="citys"
        @cleanInput="() => (this.service = false)"
        @update="getData"
      />
      <DeliveryCityList />
    </div>

    <div class="delivery__service">
      <DeliveryOrder :city="orderArray" v-if="service" />
      <DeliveryCarContent v-else />
    </div>
    <DeliveryFooter />
  </div>
</template>

<style lang="scss">
* {
  box-sizing: border-box;
  font-family: Roboto, sans-serif;
  margin: 0;
  padding: 0;
  li {
    list-style-type: none;
  }
}

.container {
  display: flex;
  flex-wrap: wrap;

  .delivery__content {
    width: 100%;
    max-width: 50%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 0 5% 0 10%;
  }

  .delivery__service {
    width: 100%;
    max-width: 50%;
    position: relative;
    background-color: #f7f7f7;
    border-radius: 40px 0 0 40px;
  }
}

/* Медиа-запросы для адаптивности */

@media (max-width: 320px) {
  .container {
    display: flex;
    flex-direction: column;

    .delivery__content {
      margin: 0 25px;
      max-width: 100%;
    }

    .delivery__service {
      display: flex;
      justify-content: center;
      width: 100%;
      max-width: 320px;
      border-radius: 40px 40px 0 0;
    }
  }
}
</style>
