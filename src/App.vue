<template>
  <div class="p-8 bg-gray-100 min-h-screen">
    <h1 class="text-4xl font-bold mb-8 text-center text-gray-800">
      Design System Demo With Vue 3 and Tailwind CSS
    </h1>

    <!-- Buttons Section -->
    <section class="mb-12 bg-white p-6 rounded-lg shadow-md">
      <h2 class="text-2xl font-semibold mb-4 text-gray-700">Buttons</h2>
      <div class="flex flex-wrap gap-4">
        <Button variant="primary" @click="handleClick">Primary</Button>
        <Button variant="secondary" @click="handleClick">Secondary</Button>
        <Button variant="success" @click="handleClick">Success</Button>
        <Button variant="danger" @click="handleClick" showClicks>Danger</Button>
      </div>
    </section>

    <!-- Input Section -->
    <section class="mb-12 bg-white p-6 rounded-lg shadow-md">
      <h2 class="text-2xl font-semibold mb-4 text-gray-700">Input</h2>
      <Input v-model="inputValue" :minLength="5" />
      <p class="mt-2">Current input: {{ inputValue }}</p>
    </section>

    <!-- Cards Section -->
    <section class="mb-12 bg-white p-6 rounded-lg shadow-md">
      <h2 class="text-2xl font-semibold mb-4 text-gray-700">Cards</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <Card
          v-for="(card, index) in cards"
          :key="index"
          :title="card.title"
          :imageUrl="card.image"
        >
          <p>{{ card.description }}</p>
        </Card>
      </div>
    </section>

    <!-- Modal Section -->
    <section class="mb-12 bg-white p-6 rounded-lg shadow-md">
      <h2 class="text-2xl font-semibold mb-4 text-gray-700">Modal</h2>
      <Button @click="isModalOpen = true">Open Modal</Button>
      <Modal v-model="isModalOpen">
        <h2 class="text-2xl font-bold mb-4">Modal Title</h2>
        <p>This is an example of the Modal component in action.</p>
      </Modal>
    </section>
  </div>
</template>

<script setup>
import Button from "@/components/Button.vue";
import Card from "@/components/Card.vue";
import Input from "@/components/Input.vue";
import Modal from "@/components/Modal.vue";

import { ref } from "vue";

const handleClick = (clickCount) => {
  console.log(`Button clicked ${clickCount} times`);
};

const inputValue = ref("");

const cards = ref([
  {
    title: "Mountain View",
    description: "A beautiful landscape with mountains and a lake.",
    image: "/api/placeholder/800/600",
  },
  {
    title: "City Nights",
    description: "A vibrant cityscape illuminated at night.",
    image: "/api/placeholder/800/600",
  },
  {
    title: "Beach Sunset",
    description: "A serene beach scene with a colorful sunset.",
    image: "/api/placeholder/800/600",
  },
]);

const isModalOpen = ref(false);
</script>
