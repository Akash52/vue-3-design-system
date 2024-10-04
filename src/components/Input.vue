<!-- Input.vue -->
<template>
  <div class="relative">
    <input
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      type="text"
      class="w-full px-4 py-2 border rounded-md"
      :class="{
        'border-green-500': isValid,
        'border-red-500': !isValid && modelValue,
      }"
      :style="{
        transition: 'all 0.3s ease',
        boxShadow: isValid ? '0 0 0 2px rgba(72, 187, 120, 0.2)' : 'none',
      }"
    />
    <span
      class="absolute right-3 top-2"
      :class="{
        'text-green-500': isValid,
        'text-red-500': !isValid && modelValue,
      }"
    >
      {{ isValid ? '✓' : '✗' }}
    </span>
  </div>
  <p
    class="text-sm mt-1"
    :class="{
      'text-green-600': isValid,
      'text-red-600': !isValid && modelValue,
    }"
  >
    {{ feedback }}
  </p>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  modelValue: {
    type: String,
    default: '',
  },
  minLength: {
    type: Number,
    default: 5,
  },
});

const emit = defineEmits(['update:modelValue']);

const isValid = computed(() => props.modelValue.length >= props.minLength);

const feedback = computed(() => {
  if (!props.modelValue) return 'Please enter some text';
  return isValid.value
    ? 'Valid input!'
    : `Input must be at least ${props.minLength} characters long`;
});
</script>
