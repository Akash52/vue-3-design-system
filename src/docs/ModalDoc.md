# Modal Component

The Modal component is a customizable overlay for displaying content on top of the main page.

## Usage

```vue
<template>
  <Button @click="isModalOpen = true">Open Modal</Button>
  <Modal v-model="isModalOpen">
    <h2 class="text-2xl font-bold mb-4">Modal Title</h2>
    <p>This is the modal content.</p>
  </Modal>
</template>

<script setup>
import { ref } from 'vue';
import { Button, Modal } from '@/components';

const isModalOpen = ref(false);
</script>
```

## Props

| Prop         | Type    | Default  | Description                                             |
| ------------ | ------- | -------- | ------------------------------------------------------- |
| `modelValue` | Boolean | Required | Controls the visibility of the modal (use with v-model) |

## Events

| Event               | Payload   | Description                               |
| ------------------- | --------- | ----------------------------------------- |
| `update:modelValue` | `Boolean` | Emitted when the modal visibility changes |

## Slots

| Slot    | Description                                  |
| ------- | -------------------------------------------- |
| default | The content to be displayed inside the modal |

## Styling

The Modal component uses Tailwind CSS classes for styling. It includes a semi-transparent overlay and a centered content area.

## Animations

The modal has smooth enter and leave transitions, implemented using Vue's `<Transition>` component and CSS transitions.

## Notes

- The Modal component uses Vue's `<Teleport>` feature to render the modal outside the current component tree, directly in the `<body>` tag.
- It includes a close button that emits the `update:modelValue` event to close the modal.
