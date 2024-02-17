<script setup>
import sourceData from '@/data.json'
import { computed } from 'vue'

const props = defineProps({
  id: {
    type: Number,
    required: true
  },
  experienceSlug: {
    type: String,
    required: true
  }
})

const destination = computed(() => sourceData.destinations.find(dest => dest.id === props.id))
const experience = computed(() => destination.value.experiences.find(exp => exp.slug === props.experienceSlug))
</script>

<template>
  <section>
    <h1>{{ experience.name }}</h1>
    <img :src="`/images/${experience.image}`" :alt="experience.name">
    <p>{{ experience.description }}</p>
  </section>
</template>

<style scoped>

</style>