<script lang="ts">
import { defineComponent, type PropType } from 'vue'

interface State {
  inputText: string
  toggler: boolean
}

export default defineComponent({
  props: {
    cityInputError: {
      type: Boolean as PropType<Boolean>,
      required: true
    },
    complitedCityArr: {
      type: Array
    }
  },
  data(): State {
    return {
      inputText: '',
      toggler: true
    }
  },
  watch: {
    // inputText(newVal) {
    //   if (this.cityInputError && this.inputText === '') {
    //     return this.clearForm()
    //   }
    //   console.log(newVal)
    // }
  },
  methods: {
    submitForm() {
      console.log('submitForm work')
      this.$emit('submitForm', this.inputText)
    },
    clearForm() {
      this.inputText = ''
      console.log('clearForm work')
      this.$emit('clearForm', this.cityInputError)
    }
  },
  emits: {
    submitForm: (text: string) => typeof text === 'string',
    clearForm: Boolean
  }
})
</script>
<template>
  <div class="delivery__form-container" :class="cityInputError ? ' errorClass' : ''">
    <form @submit.prevent class="delivery__form">
      <input v-model="inputText" type="text" placeholder="Enter name of the city" />
      <button @click="submitForm" v-if="!cityInputError && complitedCityArr?.length === 0">
        ENTER
      </button>
      <button @click="clearForm" :class="{ oBtn: !cityInputError }" v-else>X</button>
    </form>
    <span v-if="cityInputError">We didn’t found such city. Please check spelling</span>
  </div>
</template>
