# Card Component

The Card component is a flexible container for displaying content with an optional image.

## Usage

```vue
<template>
  <Card title="Example Card" imageUrl="/path/to/image.jpg">
    <p>This is the card content.</p>
  </Card>
</template>

<script setup>
import { Card } from '@/components';
</script>
```

## Props

| Prop       | Type   | Default  | Description                                        |
| ---------- | ------ | -------- | -------------------------------------------------- |
| `title`    | String | Required | The title of the card                              |
| `imageUrl` | String | `''`     | URL of the image to display at the top of the card |

## Slots

| Slot    | Description                                 |
| ------- | ------------------------------------------- |
| default | The content to be displayed inside the card |

## Styling

The Card component uses Tailwind CSS classes for styling. It includes a hover effect that slightly raises the card and increases its shadow.

## Animations

The card has a smooth transition effect when hovered, implemented using Vue's reactive properties and inline styles.
