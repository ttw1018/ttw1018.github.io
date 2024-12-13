<template>
  <h1>
    Education
  </h1>

  <el-col :span="24" v-for="edu in education">
    <el-card width="100%" shadow="hover">
      <div>
        <h3>{{ edu.university }}</h3>
        <h5>
          {{ edu.degree }}
          <el-divider direction="vertical" />
          {{ edu.major }}
          <el-divider direction="vertical" />
          {{ edu.timeline }}
        </h5>
      </div>
    </el-card>

  </el-col>

</template>

<script setup>
import { onMounted, ref } from 'vue'

const education = ref([])

const load_data = () => {
  fetch("data/education.json").then(res => res.json()).then(data => {
    education.value = data
  }).catch(err => {
    console.error(err)
  })
}

onMounted(() => {
  load_data()
})

</script>
