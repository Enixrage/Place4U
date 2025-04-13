<template>
    <div class="bg-white p-4 rounded shadow">
      <label class="block text-sm font-medium mb-1">{{ label }}</label>
      <input
        type="text"
        class="w-full border border-gray-300 rounded p-2"
        placeholder="Enter ZIP code"
        v-model="modelValue.name"
      />
      <button
        @click="useGPS"
        class="mt-2 text-sm text-blue-600 hover:underline"
      >
        📡 Use GPS
      </button>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    modelValue: Object,
    label: String,
  })
  const emit = defineEmits(['update:modelValue'])
  
  function useGPS() {
    navigator.geolocation.getCurrentPosition((position) => {
      const coords = position.coords
      emit('update:modelValue', {
        ...props.modelValue,
        name: `Lat: ${coords.latitude.toFixed(2)}, Lon: ${coords.longitude.toFixed(2)}`,
      })
  
      // Fake data — replace this with your API call
      setTimeout(() => {
        emit('update:modelValue', {
          ...props.modelValue,
          name: `GPS (${coords.latitude.toFixed(2)}, ${coords.longitude.toFixed(2)})`,
          air: Math.floor(Math.random() * 100),
          water: Math.floor(Math.random() * 100),
          crime: Math.floor(Math.random() * 100),
        })
      }, 1000)
    })
  }
  </script>
  