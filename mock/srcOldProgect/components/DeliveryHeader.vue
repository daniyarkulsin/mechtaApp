<template>
  <div>
    <div class="delivery__header">
      <img src="@/img/logo.svg" alt="logo" />
      <h2>FastService</h2>
    </div>
    <div class="delivery__main">
      <h1>Delivery cost</h1>
      <p>Enter name of the city to count delivery cost</p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DeliveryHeader',
}
</script>
<style lang="scss">
.delivery__header {
  display: flex;
  align-items: center;
  margin: 20px 0 80px;
  h2 {
    margin-left: 15px;
  }
}
.delivery__main {
  h1 {
    font-size: 48px;
    line-height: 56.25px;
    margin-bottom: 15px;
  }
  p {
    font-size: 24px;
    color: #28304480;
  }
}

@media (max-width: 320px) {
  .delivery__header {
    margin: 20px 0 50px;

    h2 {
      margin-left: 15px;
    }
  }
  .delivery__main {
    margin-bottom: 40px;
    h1 {
      font-size: 36px;
      margin-bottom: 20px;
    }
    p {
      max-width: 200px;
      font-size: 16px;
      color: #28304480;
    }
  }
}
</style>
