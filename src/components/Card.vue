<!-- Card.vue -->
<template>
  <div
    class="bg-white rounded-lg overflow-hidden shadow-lg"
    :style="{
      transition: 'all 0.3s ease',
      transform: isHovered ? 'translateY(-5px)' : 'translateY(0)',
      boxShadow: isHovered
        ? '0 10px 20px rgba(0,0,0,0.2)'
        : '0 4px 6px rgba(0,0,0,0.1)',
    }"
    @mouseenter="isHovered = true"
    @mouseleave="isHovered = false"
  >
    <img
      v-if="imageUrl"
      :src="imageUrl"
      :alt="title"
      class="w-full h-48 object-cover"
    />
    <div class="p-4">
      <h3 class="text-xl font-semibold mb-2">{{ title }}</h3>
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

defineProps({
  title: {
    type: String,
    required: true,
  },
  imageUrl: {
    type: String,
    default: '',
  },
});

const isHovered = ref(false);
</script>
