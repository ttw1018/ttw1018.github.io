<template>
  <h1>Introduction</h1>
  <el-card width="100%" shadow="hover">
    <p>{{ introduction.introduction }}</p>
  </el-card>
</template>

<script setup>
import { ref, onMounted } from "vue";

const introduction = ref({});

const load_introduction = () => {
  fetch("data/introduction.json")
    .then((res) => res.json())
    .then((data) => {
      introduction.value = data;
      // console.log(introduction.value)
    })
    .catch((err) => {
      console.log(err);
    });
};

onMounted(() => {
  load_introduction();
});
</script>
