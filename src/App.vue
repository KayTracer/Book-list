<script setup>
import Progress from "./components/Progress.vue";
import { ref, reactive } from "vue";

let courses = reactive([
  {
    title: "Tantra",
    done: true,
  },
  {
    title: "Vue.js",
    done: true,
  },
  {
    title: "Python",
    done: false,
  },
]);

let newCourse = { done: false };

function addCourse() {
  courses.push(newCourse);
  newCourse = { done: false };
}
</script>

<template>
  <div>
    <h1>Lista de Cursos</h1>
    <ul>
      <li v-for="course in courses" :key="course.title">{{ course.title }}</li>
    </ul>
    <input type="text" v-model="newCourse.title" />
    <button @click="addCourse()">Add new Course</button>
  </div>
  <Progress :courses="courses" />
</template>

<style scoped></style>
