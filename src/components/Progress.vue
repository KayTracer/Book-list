<script setup>
import { computed } from "vue";
const props = defineProps(["courses"]);

const coursesDone = computed(() => {
  return props.courses.filter((course) => course.done);
});
</script>

<template>
  <div>
    {{
      `${coursesDone.length} cursos concluídos de um total de: ${courses.length}`
    }}
  </div>
</template>
