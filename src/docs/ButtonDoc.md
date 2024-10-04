# Button Component

The Button component is a versatile and customizable button that can be used throughout your application.

## Usage

```vue
<template>
  <Button variant="primary" @click="handleClick">
    Click me
  </Button>
</template>

<script setup>
import { Button } from '@/components';

const handleClick = (clickCount) => {
  console.log(`Button clicked ${clickCount} times`);
};
</script>
```

## Props

| Prop         | Type    | Default     | Description                                                                                          |
| ------------ | ------- | ----------- | ---------------------------------------------------------------------------------------------------- |
| `variant`    | String  | `'primary'` | The visual style of the button. Options are `'primary'`, `'secondary'`, `'success'`, and `'danger'`. |
| `showClicks` | Boolean | `false`     | Whether to display the number of times the button has been clicked.                                  |

## Events

| Event   | Payload  | Description                                                                                         |
| ------- | -------- | --------------------------------------------------------------------------------------------------- |
| `click` | `Number` | Emitted when the button is clicked. The payload is the number of times the button has been clicked. |

## Slots

| Slot    | Description                                    |
| ------- | ---------------------------------------------- |
| default | The content to be displayed inside the button. |

## Styling

The Button component uses Tailwind CSS classes for styling. The base styles can be customized by modifying the `baseClass` constant in the component. Variant-specific styles are defined in the `variantClass` computed property.

## Animations

The Button component includes a subtle scale animation on hover, implemented using inline styles and Vue's reactive properties.
