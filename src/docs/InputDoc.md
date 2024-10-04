# Input Component

The Input component is a customizable text input field with built-in validation.

## Usage

```vue
<template>
  <Input v-model="inputValue" :minLength="5" />
</template>

<script setup>
import { ref } from 'vue';
import { Input } from '@/components';

const inputValue = ref('');
</script>
```

## Props

| Prop         | Type   | Default | Description                                             |
| ------------ | ------ | ------- | ------------------------------------------------------- |
| `modelValue` | String | `''`    | The value of the input field (use with v-model)         |
| `minLength`  | Number | `5`     | The minimum length for the input to be considered valid |

## Events

| Event               | Payload  | Description                          |
| ------------------- | -------- | ------------------------------------ |
| `update:modelValue` | `String` | Emitted when the input value changes |

## Styling

The Input component uses Tailwind CSS classes for styling. It includes visual feedback for valid and invalid states.

## Validation

The component provides built-in validation based on the `minLength` prop. It displays a checkmark for valid input and an "x" for invalid input, along with appropriate feedback messages.
