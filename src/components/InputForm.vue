<script setup>
import { ref } from 'vue'
import { calculate, store } from '../store/store'

const total = ref(0)
const tip = ref(0)
const people = ref(0)

const handleSubmit = () => {
  store.params.total = total
  store.params.tip = tip
  store.params.people = people
  calculate()
}

</script>

<template>
  <form @submit.prevent="handleSubmit">
    <div class="form-container">
      <div>
        <label for="total">Total</label>
        <input type="number" required v-model="total">
      </div>
      <div>
        <label for="tip">Tip %</label>
        <input type="number" required v-model="tip">
      </div>
      <div>
        <label for="people">People</label>
        <input type="number" required v-model="people">
      </div>

      <div>
        <input type="submit" value="Calculate">
      </div>
    </div>
  </form>
</template>

<style scoped></style>