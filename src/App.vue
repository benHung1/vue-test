<script setup>
import { reactive } from 'vue'
import axios from 'axios'
import FormButtons from './components/FormButton.vue'
import RecordTable from './components/RecordTable.vue'

const apiUrl = 'http://nexifytw.mynetgear.com:45000/api/Record'

const state = reactive({
  records: [],
  errorMsg: 'Oops...something wrong, please try again later...'
})

// update
const getData = async () => {
  try {
    const res = await axios.get(`${apiUrl}/GetRecords`)
    state.records = res.data.Data.map((item) => ({
      ...item,
      DateOfBirth: formatDate(item.DateOfBirth)
    }))
  } catch (err) {
    alert(state.errorMsg)
  }
}

// date
const formatDate = (datetime) => {
  return datetime.split('T')[0]
}

// add
const addRow = () => {
  state.records.unshift({
    Name: '',
    DateOfBirth: '2020-01-01',
    Salary: 55000,
    Address: ''
  })
}

// save
const postData = async () => {
  try {
    await axios.post(`${apiUrl}/SaveRecords`, state.records)
    getData()
  } catch (err) {
    alert(state.errorMsg)
  }
}
</script>

<template>
  <header>
    <FormButtons :addRow="addRow" :saveData="postData" :updateData="getData" />
  </header>

  <RecordTable :records="state.records" />
</template>
