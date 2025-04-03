<template>
  <h1>Experiences</h1>
  <el-col :span="24" v-for="experience in experiences">
    <el-card width="100%" shadow="hover">
      <div>
        <h3>{{ experience.jobTitle }}</h3>
        <h5>
          {{ experience.type }}
          <el-divider direction="vertical" />
          {{ experience.company }}
          <el-divider direction="vertical" />
          {{ experience.timeline }}
        </h5>
        <div v-for="desc in experience.description">
          <p>{{ desc }}</p>
        </div>
      </div>
    </el-card>
  </el-col>
</template>

<script setup>
import { onMounted, ref } from "vue";

const experiences = ref([]);

const load_data = () => {
  fetch("data/experiences.json")
    .then((res) => res.json())
    .then((data) => {
      experiences.value = data;
      // console.log(data)
    })
    .catch((err) => {
      console.error(err);
    });
};

onMounted(() => {
  load_data();
});
</script>
