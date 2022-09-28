<template>
  <div>
    <h1 v-bind:class="isAvailable ? 'isAvailable' : 'other-color'">
      {{ 2 + 2 }}
    </h1>
    <hr />
    <div>
      <h2 v-if="showElement === true">The Product is available</h2>
      <h2 v-else>The Product is not available</h2>
    </div>
    <div v-for="(post, index) in postData" :key="index" class="iteration">
      <h3>{{ index + 1 }} - {{ post.title }}</h3>
      <p>
        {{ post.description }}
      </p>
      <p>
        {{ post.duration }}
      </p>
    </div>
    <hr />
    <div class="colorButton">
      <button @click="changeColor">Click me! to see changes</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const showElement = ref(true);

const postData = ref([
  {
    title: "Avatar",
    description: "A sciencie fiction movie",
    duration: "120 mins",
  },
  {
    title: "The Prestige",
    description: "A Thriller and Suspense movie",
    duration: "130 mins",
  },
  {
    title: "Pulp Fiction",
    description: "A cult film",
    duration: "153 mins",
  },
]);

const isAvailable = ref(true);

const newColor = ref({
  backgroundColor: "red",
});
function changeColor() {
  isAvailable.value = !isAvailable.value;
}
</script>

<style>
.iteration {
  margin-top: 20px;
}
h1 {
  margin-top: 30px;
  font-size: 40px;
  text-align: center;
  color: aliceblue;
}
h2 {
  margin-top: 20px;
  text-align: center;
  font-size: 30px;
}
h3 {
  font-size: 30px;
}

button {
  background-color: aqua;
  padding: 10px;
  border-radius: 10px;
  width: 150px;
  height: 200px;
  margin-top: 20px;
}
.colorButton {
  display: flex;
  justify-content: center;
}

.iteration p {
  font-size: 15px;
}

.isAvailable {
  background-color: green;
}

.other-color {
  background-color: red;
}
</style>
