<script setup lang="ts">
import Hero from "@/components/Hero.vue";
import HeroCards from "@/components/HeroCards.vue";
import JobsListings from "@/components/JobsListings.vue";
</script>

<template>
  <Hero
    title="Become a Vue Dev"
    description="Find the Vue job that fits your skills and needs"
  />

  <HeroCards />

  <JobsListings :limit="3" showButton />
</template>
