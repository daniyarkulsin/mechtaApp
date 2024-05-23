<template>
  <div>
    <div class="delivery__form" :class="cityError ? ' errorClass' : ''">
      <input v-model="inputText" type="text" placeholder="Enter name of the city" />
      <button @click="inputBtn">
        {{ !cityError ? 'ENTER' : 'X' }}
      </button>
    </div>
    <span :class="cityError ? 'offOpacity' : ''"
      >We didn’t found such city. Please check spelling</span
    >
  </div>
</template>
<script>
export default {
  name: 'DeliveryForm',
  props: {
    citys: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      inputText: '',
      cityError: false
    }
  },
  methods: {
    addCity() {
      console.log('addCity')
      const newText = this.inputText.trim().toLocaleLowerCase()
      if (this.citys.find((city) => newText === city)) {
        this.$emit('update', newText)
        this.cityError = false
      } else {
        this.$emit('update', newText)
        this.cityError = true
      }
    },
    cleanInput() {
      console.log('cleanInput')
      this.inputText = ''
      this.cityError = false
      this.$emit('cleanInput', this.cityError)
    },
    updateInput() {
      return (this.cityError = false)
    },
    inputBtn() {
      !this.cityError ? this.addCity() : this.cleanInput()
    }
  },
  watch: {
    inputText(newVal) {
      console.log(newVal)
      if (this.cityError) {
        return (this.cityError = false)
      }
    }
  }
}
</script>
<style scoped lang="scss">
span {
  display: block;
  opacity: 0;
  margin: 10px;
  color: rgba(255, 71, 87, 1);
}
.offOpacity {
  opacity: 1;
}

.delivery__form {
  width: 100%;
  max-width: 520px;
  height: 60px;
  border-radius: 50px;
  display: flex;
  border: 1px solid #e6e6e6;
  input {
    flex-grow: 1; /* Поле занимает всё доступное пространство */
    border: none; /* Границы отсутствуют */
    padding: 5px;
    outline: none; /* Очертание при фокусе отсутствует */
    padding-left: 30px;
    border-radius: 50px;
    padding-top: 10px;
    &::placeholder {
      color: rgba(217, 228, 220, 1);
      font-size: 24px;
    }
    &:focus {
      padding-top: 0;
    }
  }
  button {
    width: 100%;
    max-width: 170px;
    border: none;
    padding: 5px;
    cursor: pointer;
    border-radius: 35px;
    color: #fff;
    font-size: 24px;
    font-weight: 700;
    background: linear-gradient(279.56deg, #65b3e4 15.15%, rgba(120, 161, 187, 0) 171.55%);
  }
}
.errorClass {
  border: 1px solid rgba(255, 71, 87, 1);
  button {
    width: 100%;
    max-width: 65px;
    background: linear-gradient(279.56deg, rgb(255, 71, 87) 15.15%, rgba(255, 255, 255, 0) 171.55%);
  }
}

@media (max-width: 320px) {
  span {
    font-size: 12px;
    width: 320px;
  }
  .offOpacity {
    opacity: 1;
  }

  .delivery__form {
    width: 270px;
    height: 50px;
    input {
      &::placeholder {
        color: rgba(217, 228, 220, 1);
        font-size: 16px;
      }
    }
    button {
      font-size: 14px;
      padding: 0 10px;
    }
  }
}
</style>
