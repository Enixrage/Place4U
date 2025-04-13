<template>
    <tr>
      <td class="p-2 font-medium">{{ label }}</td>
      <td class="p-2 text-center">{{ a ?? '–' }}</td>
      <td class="p-2 text-center">{{ b ?? '–' }}</td>
    </tr>
  </template>
  
  <script setup>
  defineProps({
    label: String,
    a: Number,
    b: Number,
  })
  </script>
  