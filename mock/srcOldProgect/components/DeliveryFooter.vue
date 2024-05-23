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
<script>
export default {
  name: 'delivery-footer',
}
</script>
<style scoped lang="scss">
.delivery__footer {
  display: flex;
  justify-content: space-between;
  margin-top: -50px;
  margin-left: 10%;
  width: 100%;
  max-width: 30%;
  h5 {
    color: rgba(40, 48, 68, 0.5);
    max-width: 140px;
  }
  img {
    margin-right: 10px;
    &:last-child {
      margin: 0;
    }
  }
}
@media (max-width: 320px) {
  .delivery__footer {
    flex-direction: column-reverse;
    margin: 25px 0 25px 25px;
    max-width: 100%;
    h5 {
      margin-top: 20px;
    }
  }
}
</style>
