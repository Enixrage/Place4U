<template>
    <div class="min-h-screen bg-gray-100 p-6">
      <h1 class="text-2xl font-bold mb-6 text-center">🌍 Compare Locations</h1>
  
      <!-- Location Inputs -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-8">
        <LocationInput v-model="locationA" label="Location A" />
        <LocationInput v-model="locationB" label="Location B" />
      </div>
  
      <!-- Score Comparison -->
      <div class="bg-white shadow rounded-lg p-6">
        <h2 class="text-xl font-semibold mb-4">📊 Score Comparison</h2>
        <table class="w-full text-left border-collapse">
          <thead>
            <tr class="text-gray-600">
              <th class="p-2">Category</th>
              <th class="p-2">{{ locationA.name || "Location A" }}</th>
              <th class="p-2">{{ locationB.name || "Location B" }}</th>
            </tr>
          </thead>
          <tbody>
            <CompareRow
              label="Air Quality"
              :a="locationA.air"
              :b="locationB.air"
            />
            <CompareRow
              label="Water Quality"
              :a="locationA.water"
              :b="locationB.water"
            />
            <CompareRow
              label="Crime Rate"
              :a="locationA.crime"
              :b="locationB.crime"
            />
          </tbody>
        </table>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import LocationInput from './LocationInput.vue'
  import CompareRow from './CompareRow.vue'
  
  const locationA = ref({
    name: '',
    air: null,
    water: null,
    crime: null,
  })
  
  const locationB = ref({
    name: '',
    air: null,
    water: null,
    crime: null,
  })
  </script>
  