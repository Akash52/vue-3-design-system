<!-- Modal.vue -->
<template>
  <Teleport to="body">
    <Transition name="modal">
      <div
        v-if="modelValue"
        class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4"
      >
        <div
          class="bg-white rounded-lg max-w-md w-full"
          :style="{
            transform: modelValue ? 'scale(1)' : 'scale(0.9)',
            opacity: modelValue ? 1 : 0,
            transition: 'all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55)',
          }"
        >
          <div class="p-6">
            <slot></slot>
            <div class="flex justify-end mt-4">
              <Button
                @click="$emit('update:modelValue', false)"
                variant="danger"
              >
                Close
              </Button>
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<script setup>
import { Button } from './Button.vue';

defineProps({
  modelValue: {
    type: Boolean,
    required: true,
  },
});

defineEmits(['update:modelValue']);
</script>

<style scoped>
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}
</style>
