
<template>
    <div>
      <input type="text" :value="modelValue" @input="handleInput">
      <ul v-show="searchResults.length && isOpen">
        <li class="des" v-for="result in searchResults" :key="result.name" @click="setSelected(result.name)">
          {{ result.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  
  const props = defineProps({
    source: { type: Array, required: true, default: () => [] },
    modelValue: String
  })
  const emit = defineEmits(['update:modelValue'])
  
  const search = ref('')
  const searchResults = computed(() => search.value === '' ? [] : props.source.filter(item => item.name.toLowerCase().includes(search.value.toLowerCase())))
  
  const isOpen = ref(false)
  
  const setSelected = item => {
    isOpen.value = false
    search.value = item
    emit('update:modelValue', search.value)
  }
  
  const handleInput = event => {
    isOpen.value = true
    search.value = event.target.value
    emit('update:modelValue', search.value)
  }
  </script>
  