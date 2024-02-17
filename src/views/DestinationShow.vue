<script setup>
import { computed } from 'vue'
import sourceData from '@/data.json'
import ExperienceCard from '@/components/ExperienceCard.vue'
import GoBack from '@/components/GoBack.vue'

const props = defineProps({
  id: {
    type: Number,
    required: true
  },
})
// 1. 从本地获取数据
const destination = computed(() => sourceData.destinations.find(dest => dest.id === props.id))
</script>

<template>
  <div>
    <section v-if="destination" class="destination">
      <h1>{{ destination.name }}</h1>
      <GoBack />
      <div v-if="destination" class="destination-details">
        <img :src="`/images/${destination.image}`" :alt="destination.name">
        <p>{{ destination.description }}</p>
      </div>
    </section>
    <section class="experiences">
      <h2>Top Experiences in {{ destination.name }}</h2>
      <div class="cards">
        <router-link v-for="experience in destination.experiences" :key="experience.slug"
                     :to="{name: 'experience.show', params: {experienceSlug: experience.slug}}">
          <ExperienceCard :experience="experience" />
        </router-link>
      </div>
      <router-view />
    </section>
  </div>
</template>

<style scoped>

</style>