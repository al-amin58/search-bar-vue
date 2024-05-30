<script setup>
import Autocomplete from '@/components/Autocomplete.vue';
import countries from '@/data/countries.json'
import{ref} from 'vue'
const country = ref('')
</script>

<template>
  <main>
    <h1>Selectd:{{ country }}</h1>
    <Autocomplete :source="countries" v-model="country"/>
  </main>
</template>
