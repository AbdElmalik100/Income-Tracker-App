<script setup>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import IncomeList from './components/incomeList.vue';

import { ref, reactive, computed } from 'vue'

const state = reactive({
  income: [],
  totalIncome: computed(() => {
    let temp = 0
    if (state.income.length) {
      for (let i = 0; i < state.income.length; i++) {
        temp += state.income[i].value
      }
    }
    return temp
  }),
  sortedIncome: computed(() => {
    let temp = []
    temp = state.income.sort((a, b) => {
      return b.date.getTime() - a.date.getTime()
    })
    return temp
  })
})

function addIcome(data) {
  state.income.push({
    id: Date.now(),
    desc: data.desc,
    value: data.value,
    date: new Date(data.date)
  })
}

function removeItem(element) {
  state.income = state.income.filter(el => el != element)
}

</script>

<template>
  <div>
    <Header :totalIncome="state.totalIncome"></Header>
    <Form @add-income="addIcome"></Form>
    <income-list :state="state" @remove-item="removeItem"></income-list>
  </div>
</template>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #eee;
}
</style>
