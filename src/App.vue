<script setup>
import TheNavigation from '@/components/TheNavigation.vue'
import { useRoute } from 'vue-router'

const route = useRoute()
</script>

<template>
  <TheNavigation />
  <div class="container">
    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" :key="route.path"></component>
      </transition>
    </router-view>
  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
