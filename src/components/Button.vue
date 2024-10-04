<!-- Button.vue -->
<template>
  <button
    :class="[baseClass, variantClass]"
    :style="{
      transition: 'all 0.3s ease',
      transform: isHovered ? 'scale(1.05)' : 'scale(1)',
    }"
    @mouseenter="isHovered = true"
    @mouseleave="isHovered = false"
    @click="handleClick"
  >
    <slot></slot>
    <span v-if="showClicks" class="ml-2">({{ clicks }})</span>
  </button>
</template>

<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) =>
      ['primary', 'secondary', 'success', 'danger'].includes(value),
  },
  showClicks: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(['click']);

const isHovered = ref(false);
const clicks = ref(0);

const baseClass =
  'px-4 py-2 rounded font-semibold text-white transition-colors duration-300';

const variantClass = computed(() => {
  const variants = {
    primary: 'bg-blue-500 hover:bg-blue-600',
    secondary: 'bg-gray-500 hover:bg-gray-600',
    success: 'bg-green-500 hover:bg-green-600',
    danger: 'bg-red-500 hover:bg-red-600',
  };
  return variants[props.variant];
});

const handleClick = () => {
  clicks.value++;
  emit('click', clicks.value);
};
</script>
