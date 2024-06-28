<script setup>
import { defineProps } from 'vue'

defineProps({
  addRow: {
    type: Function,
    required: true
  },
  saveData: {
    type: Function,
    required: true
  },
  updateData: {
    type: Function,
    required: true
  }
})
</script>

<template>
  <div class="button-group">
    <button @click="addRow" class="add-btn">Add</button>
    <button @click="saveData" class="save-btn">Save</button>
    <button @click="updateData" class="update-btn">Update</button>
  </div>
</template>

<style lang="scss" scoped>
.button-group {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
  .add-btn {
    background: blue;
  }

  .save-btn {
    background: green;
  }

  .update-btn {
    background: red;
  }
}
</style>
