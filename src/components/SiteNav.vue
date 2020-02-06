<template>
  <nav class="mx-4 flex justify-center">
    <div class="flex">
      <router-link class="nav-link mr-4" to="/">Home</router-link>
      <router-link class="nav-link mr-4" to="/resume">Resume</router-link>
      <router-link class="nav-link mr-4" to="/skills">Skills</router-link>
      <router-link class="nav-link" to="/contact">Contact</router-link>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style lang="postcss">
.nav-link {
  @apply block px-4 py-3 uppercase;
}
.nav-link:hover {
  @apply bg-gray-100 text-teal-800 rounded-lg;
}
</style>
