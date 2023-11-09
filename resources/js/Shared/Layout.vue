<template>
  <div
    id="progress"
    class="fixed left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2"
  />
  <section class="bg-base-200">
    <Navbar />
    <slot />
  </section>
</template>

<script setup>
import Navbar from "./Navbar.vue";
</script>
