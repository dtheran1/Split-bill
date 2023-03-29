<script setup>

import { defineProps, ref } from 'vue'
import { pay } from '../store/store'
const props = defineProps(['id', 'numberOfPerson', 'totalPerPerson', 'paid'])

const paid = ref(false)

const handleChange = (e) => {
  paid.value = e.target.checked

  pay(props.id, paid.value)

}

</script>

<template>
  <div :class="['person', props.paid ? 'person-paid' : 'person-no-paid']">
    <div class="person-number">
      Person {{ props.numberOfPerson }}
    </div>
    <div class="person-to-pay">
      {{
        new Intl.NumberFormat('en-US', {
          style: 'currency',
          currency: 'USD',
        }).format(props.totalPerPerson)
      }}
    </div>

    <div class="paid">
      <input type="checkbox" @change="handleChange"> Paid
    </div>
  </div>
</template>

<style scoped>
.person{
  height: 200px;
  border-radius: 5px;
  font-size: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  overflow: hidden;
  /* padding: 20px; */
}

.person-paid{
  border: 3px solid yellowgreen;
}

.person-no-paid{
  border: 3px solid gray;
}

.person-number{
  background-color: black;
  padding: 10px;
  color: wheat;
  text-align: center;
}

.person-to-pay{
  text-align: center;
  font-size: 30px;
  font-weight: bolder;
  color: yellowgreen;
}

.paid{
  background-color: #343f68;
  padding: 10px;
}
</style>