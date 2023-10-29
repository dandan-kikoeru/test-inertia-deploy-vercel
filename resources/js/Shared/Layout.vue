<template>
  <div
    id="progress"
    class="fixed left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2"
  />
  <Navbar class="z-50"/>
  <section class="pt-16 min-h-screen bg-base-200">
    <slot />
  </section>
</template>

<script setup>
import Navbar from "./Navbar.vue";
</script>
