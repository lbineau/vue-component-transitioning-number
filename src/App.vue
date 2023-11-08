<script setup>
import { ref } from 'vue'
import TransitioningNumber from './components/TransitioningNumber.vue'
const value = ref(8)
</script>

<template>
  <div>
    <label for="number">Label: </label>
    <input type="number" name="number" id="number" v-model="value" min="0" max="9">
  </div>
  Price: <TransitioningNumber :end-value="value" />€
</template>
