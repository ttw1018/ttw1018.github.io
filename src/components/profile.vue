<template>
  <div class="ProfileInfo">
    <div class="profile-avatar">
      <el-avatar :src="profileData.avatar" :size="150"></el-avatar>
    </div>

    <div>
      <H2 class="keep-centre">{{ profileData.name }}</H2>
      <p class="keep-centre">
        <el-icon>
          <Position />
        </el-icon>
        {{ profileData.location }}
      </p>
      <p class="keep-centre">
        <el-icon>
          <Message />
        </el-icon>
        {{ profileData.email }}
      </p>
    </div>
    <div style="display: flex; justify-content: center; align-items: center">
      <el-button
        v-if="profileData['google-scholar']"
        @click="openLink(profileData['google-scholar'])"
        circle
        size="large"
      >
        <template #icon>
          <img
            src="/public/img/google-scholar.svg"
            style="width: 100%; height: 100%; object-fit: contain"
          />
        </template>
      </el-button>

      <el-button
        v-if="profileData.github"
        @click="openLink(profileData.github)"
        circle
        size="large"
      >
        <template #icon>
          <img
            src="/public/img/github.svg"
            style="width: 100%; height: 100%; object-fit: cover"
          />
        </template>
      </el-button>

      <el-button
        v-if="profileData.linkedin"
        @click="openLink(profileData.linkedin)"
        circle
        size="large"
      >
        <template #icon>
          <img
            src="/public/img/linkedin.png"
            style="width: 100%; height: 100%; object-fit: cover"
          />
        </template>
      </el-button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { Message, Position } from "@element-plus/icons-vue";

const profileData = ref({});

const openLink = (url) => {
  console.log(url);
  window.open(url, "_blank");
};

function loadProfile() {
  fetch("data/profile.json")
    .then((r) => r.json())
    .then((data) => {
      profileData.value = data;
    })
    .catch((error) => {
      console.log(error);
    });
}

onMounted(() => {
  loadProfile();
});
</script>

<style>
.profile-avatar {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.keep-centre {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
