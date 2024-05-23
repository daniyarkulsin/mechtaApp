<template>
  <form @submit.prevent class="container">
    <div v-for="cit in city" class="radiobtn" :key="cit.type" :class="{ opacity: !cit.available }">
      <label :class="{ active: selectedOption === cit.type }">
        <div>
          <input
            v-model="selectedOption"
            type="radio"
            :id="cit.type"
            name="drone"
            :value="cit.type"
          />
          <h2>{{ cit.type }}</h2>
          <h3>{{ cit.price }}$</h3>
        </div>
        <img :src="`src/img/${cit.type}.svg`" alt="#" />
      </label>
    </div>
  </form>
</template>

<script>
export default {
  name: 'DeliveryOrder',
  props: {
    city: {
      type: Array
    }
  },
  data() {
    return {
      selectedOption: ''
    }
  },
  methods: {}
}
</script>
<style scoped lang="scss">
.container {
  display: flex;
  flex-direction: column;
  padding: 12vh 4vw 0 10vh;
  .opacity {
    opacity: 0.5;
    pointer-events: none;
  }
  .active {
    box-shadow: 0 0 12px #4a7275b6;

    &::after {
      content: '';
      width: 100%;
      max-width: 90px;
      background: linear-gradient(310.04deg, #65b3e4 50.89%, rgba(255, 255, 255, 0) 121.27%);
      box-shadow: 0px 0px 20px 0px rgba(120, 161, 187, 0.384);
      border-radius: 0 20px 20px 0;
    }
  }
}

.radiobtn {
  label {
    box-shadow: 0 0 12px #5e90943d;
    display: flex;
    justify-content: space-between;
    width: 100%;
    max-width: 520px;
    height: 24vh;
    position: relative;
    border-radius: 20px;
    margin-bottom: 20px;
    cursor: pointer;

    img {
      position: absolute;
      top: 15%;
      right: 20%;
    }
    div {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      margin: 35px 0 35px 40px;
      h2 {
        font-size: 36px;
      }
      h3 {
        font-size: 50px;
        color: rgba(120, 161, 187, 1);
      }
      input {
        display: none;
      }
    }
  }
}

@media (max-width: 1200px) {
  .container {
    label {
      img {
        width: 30%;
        right: 25%;
        top: 25%;
      }
      div {
        h2 {
          font-size: 24px;
        }
        h3 {
          font-size: 36px;
        }
      }
    }
  }
}

@media (max-width: 320px) {
  .container {
    width: 100%;
    label {
      width: 270px;
      height: 172px;

      img {
        width: 68px;
        top: 20vh;
      }
      div {
        h2 {
          position: absolute;
          top: 20px;
          left: 20px;
          font-size: 24px;
        }
        h3 {
          position: absolute;
          bottom: 20px;
          left: 20px;
          font-size: 32px;
        }
      }
    }

    .active {
      box-shadow: 0 0 12px #4a7275b6;

      &::after {
        max-width: 40px;
      }
    }
  }
}
</style>
