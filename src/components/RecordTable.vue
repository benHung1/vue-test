<script setup>
import { defineProps } from 'vue'

defineProps({
  records: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Birthday</th>
        <th>Salary</th>
        <th>Address</th>
      </tr>
    </thead>
    <tbody v-if="records.length > 0">
      <tr v-for="(item, index) in records" :key="`${index}-${item.DateOfBirth}`">
        <td><input name="name" type="text" autocomplete="off" v-model.trim="item.Name" /></td>
        <td>
          <input name="date" type="date" v-model="item.DateOfBirth" />
        </td>
        <td>
          <input name="salary" type="range" min="0" max="100000" v-model.number="item.Salary" />
        </td>
        <td><input name="address" type="text" autocomplete="off" v-model.trim="item.Address" /></td>
      </tr>
    </tbody>
    <div class="empty-title" v-else>currently no data, try to updated or add something...</div>
  </table>
</template>

<style lang="scss" scoped>
table {
  width: 100%;
  border-collapse: collapse;

  .empty-title {
    margin-top: 1rem;
    padding: 0 0.5rem;
  }

  th,
  td {
    padding: 8px;
    text-align: left;
  }
}
</style>
