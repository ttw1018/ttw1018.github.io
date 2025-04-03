<template>
  <div>
    <el-container style="height: 97vh">
      <el-aside class="fixed-aside">
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
        <!-- <el-footer>
        </el-footer> -->
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
</script>

<style scoped>
.el-anchor {
  --el-anchor-font-size: 22px;
  --el-anchor-color: black;
  font-family: "Comic Sans MS", "Chalkboard SE", "Marker Felt", cursive;
}

.fixed-aside {
  width: 15%;
}
</style>
