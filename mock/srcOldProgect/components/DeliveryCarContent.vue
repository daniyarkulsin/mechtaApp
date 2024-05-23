<template>
  <div class="delivery">
    <h2>Fast Service</h2>
    <img class="img-1" src="@/img/car.svg" alt="img" />
    <img class="img-2" src="@/img/line.svg" alt="img" />
    <img class="img-3" src="@/img/road.svg" alt="img" />
  </div>
</template>
<script>
export default {
  name: 'DeliveryCarContent'
}
</script>
<style scoped lang="scss">
.delivery {
  width: 50%;
  max-width: 100%;
  position: relative;
  background-color: #f7f7f7;
  border-radius: 40px 0 0 40px;
  h2 {
    position: absolute;
    font-size: 96px;
    color: rgba(40, 48, 68, 0.1);
    top: 3vh;
    left: 95%;
  }
  .img-1 {
    position: absolute;
    z-index: 3;
    top: 14vh;
    left: 23%;
  }

  .img-2 {
    position: absolute;
    top: 29vh;
    left: 10%;
    z-index: 2;
  }

  .img-3 {
    position: absolute;
    top: 9.2vh;
    left: 4%;
    z-index: 1;
  }
}
@media (max-width: 320px) {
  .delivery {
    position: relative;
    width: 100%;
    max-width: 320px;
    h2 {
      position: absolute;
      top: 1px;
      left: 1px;
      font-size: 36px;
    }
    .img-1 {
      width: 177px;
      position: absolute;
      top: 1px;
      left: 1px;
      z-index: 3;
    }

    .img-2 {
      width: inherit;

      position: absolute;
      top: 1px;
      left: 1px;
    }

    .img-3 {
      width: inherit;
      position: absolute;
      top: 1px;
      left: 1px;
    }
  }
}
</style>
