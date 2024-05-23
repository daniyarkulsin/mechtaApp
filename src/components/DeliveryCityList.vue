<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'DeliveryCityList',
  data() {
    return {
      citys: [
        'Nur - Sultan',
        'Almaty',
        'Shymkent',
        'Atyrau',
        'Aktau',
        'Zhana Turmis',
        'Karaganda',
        'Kentau',
        'Aitei',
        'Pavlodar'
      ]
    }
  }
})
</script>
<template>
  <section class="delivery__cityList">
    <h3>Most popular sities</h3>
    <ul class="delivery__cityList-inner">
      <li class="delivery__cityList-city" v-for="city in citys" :key="city">
        <a href="#">{{ city }}</a>
      </li>
    </ul>
  </section>
</template>
