<template>
  <h1>
    Publications
  </h1>

  <el-col :span="24" v-for="pub in publications">
    <el-card width="100%" shadow="hover">
      <h4>
        {{ pub.title }}
        <el-divider v-if="pub.link" direction="vertical" />
        <el-link v-if="pub.link" :href="pub.link">[link]</el-link>
        <el-divider v-if="pub.code" direction="vertical" />
        <el-link v-if="pub.code" :href="pub.code">[code]</el-link>
      </h4>
      <p>{{ pub.authors }}</p>
      <p>{{ pub.venue }}</p>

    </el-card>
  </el-col>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const publications = ref([])
const load_data = () => {
  fetch("data/publications.json").then(res => res.json()).then(data => {
    publications.value = data
  }).catch(err => {
    console.error(err)
  })
}

onMounted(() => {
  load_data()
})

</script>
