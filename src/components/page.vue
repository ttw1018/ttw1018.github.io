<template>
  <div>
    <el-container style="height: 97vh" ref="asideRef">
      <el-aside v-show="showside" class="fixed-aside">
        <Profile />
      </el-aside>
      <el-container class="main-container">
        <el-header class="fixed-header">
          <el-anchor direction="horizontal">
            <el-anchor-link
              href="#introduction"
              title="Introduction"
              id="anchor"
            />
            <el-anchor-link href="#education" title="Education" />
            <el-anchor-link href="#experience" title="Experiences" />
            <el-anchor-link href="#publications" title="Publications" />
          </el-anchor>
        </el-header>
        <el-main class="scroll-main">
          <Profile v-show="!showside" />
          <el-divider v-show="!showside" border-style="dashed" />
          <div id="introduction">
            <Introduction id="introduction" />
          </div>
          <el-divider border-style="dashed" />
          <div id="education">
            <Education />
          </div>
          <el-divider border-style="dashed" />
          <div id="experience">
            <Experiences />
          </div>
          <el-divider border-style="dashed" />
          <div id="publications">
            <Publications />
          </div>
          <el-divider border-style="dashed" />
          <Support />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
import Profile from "./profile.vue";
import Introduction from "./introduction.vue";
import Education from "./education.vue";
import Experiences from "./experiences.vue";
import Publications from "./publications.vue";
import Support from "./support.vue";
import { onMounted, ref, nextTick } from "vue";

const asideRef = ref(null);
const showside = ref(false);

const resizeObserver = new ResizeObserver(() => {
  if (asideRef.value && asideRef.value.$el) {
    const width = asideRef.value.$el.getBoundingClientRect().width;
    if (width > 1500) {
      showside.value = true;
    } else {
      showside.value = false;
    }
  }
});

onMounted(() => {
  nextTick(() => {
    if (asideRef.value && asideRef.value.$el) {
      resizeObserver.observe(asideRef.value.$el);
    }
  });
});
</script>

<style scoped>
.el-anchor {
  --el-anchor-font-size: 22px;
  --el-anchor-color: black;
}

.fixed-aside {
  width: 15%;
}

.fixed-header {
  height: 30px;
}
</style>
