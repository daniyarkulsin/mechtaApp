<template>
  <section class="delivery__section">
    <h3>Most popular sities</h3>
    <ul>
      <li v-for="city in citys" :key="city">
        <a href="#">{{ city }}</a>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
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
        'Pavlodar',
      ],
    }
  },
}
</script>
<style scoped lang="scss">
.delivery__section {
  margin-bottom: 110px;
  ul {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    max-height: 305px;
    margin-top: 30px;
    li {
      margin-right: 10px;
      a {
        color: #28304480;
        width: 100%;
        max-width: 220px;
        font-size: 20px;
        display: inline-block;
        text-decoration: none;
        padding-left: 10px;
        padding-bottom: 10px;
        margin-top: 24px;
        border-bottom: 1px solid #e6e6e6;
        &:hover {
          color: #123eacfd;
        }
      }
    }
  }
}

@media (max-width: 320px) {
  .hideDelivery__section {
    display: none;
  }
}
</style>
