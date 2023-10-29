<template>
  <div class="fixed w-screen z-50">
    <div class="navbar bg-base-100" :style="{ '--tw-bg-opacity': navOpacity }">
      <div class="flex-1">
        <Link href="/" class="btn btn-ghost normal-case text-xl">Home</Link>
      </div>
      <button class="btn btn-square btn-ghost" @click="toggleNavLink">
        <span class="material-symbols-outlined"> menu </span>
      </button>
    </div>
    <ul
      id="navlink"
      class="p-2 shadow menu bg-base-100 rounded-box w-52 absolute right-0 m-4"
      v-if="showNavLink"
    >
      <li>
        <Link href="/" :class="{ active: $page.component === 'Home' }"
          >Home</Link
        >
      </li>
      <li>
        <Link href="/contact" :class="{ active: $page.component === 'Contact' }"
          >Contact</Link
        >
      </li>
      <li>
        <Link href="/about" :class="{ active: $page.component === 'About' }"
          >About</Link
        >
      </li>
    </ul>
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue";

const showNavLink = ref(false);
const navOpacity = ref(0);

onMounted(() => {
  window.addEventListener("scroll", () => {
    const scrollY = window.scrollY;
    const maxScroll = 320;
    navOpacity.value = Math.min(scrollY / maxScroll, 1);
  });
});

const handleClick = (e) => {
  if (e.target !== document.getElementById("navlink")) {
    showNavLink.value = false;
    document.removeEventListener("click", handleClick);
  }
};

const toggleNavLink = () => {
  showNavLink.value = !showNavLink.value;
  setTimeout(() => {
    if (showNavLink.value) {
      return document.addEventListener("click", handleClick);
    }
  }, 100);
};
</script>
