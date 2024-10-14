<template>
  <div :class="cardClass" class="user-card">
    <img :src="user.photo" class="user-photo" />
    <h2>{{ user.firstName }} {{ user.lastName }}</h2>

    <!-- Show age only if it's greater than 18 -->
    <p v-if="user.age > 18">Age: {{ user.age }}</p>

    <!-- List hobbies using v-for -->
    <h3>Hobbies:</h3>
    <ul>
      <li v-for="hobby in user.hobbies" :key="hobby">{{ hobby }}</li>
    </ul>

    <p>Position: {{ user.position }}</p>
    <p>Gender: {{ user.gender }}</p>
  </div>
</template>

<script setup lang="ts">
import { defineProps, computed } from "vue";

// Define props to receive user data
const props = defineProps<{
  user: {
    firstName: string;
    lastName: string;
    age: number;
    gender: string;
    position: string;
    photo: string;
    hobbies: string[];
  };
}>();

// Determine the card color based on age
const cardClass = computed(() => {
  return props.user.age > 18 ? "card-adult" : "card-minor";
});
</script>

<style scoped>
.user-card {
  width: 300px;
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  margin: 16px;
}

.user-photo {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}

.card-adult {
  background-color: lightgreen; /* Change this color as per preference */
}

.card-minor {
  background-color: lightcoral; /* Change this color as per preference */
}
</style>
