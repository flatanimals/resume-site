<template>
  <nav class="flex justify-center w-full bg-orange-500 border-b border-orange-700">
    <div class="flex justify-around">
      <router-link class="nav-link mr-2" to="/">Home</router-link>
      <router-link class="nav-link mr-2" to="/resume">Resume</router-link>
      <router-link class="nav-link mr-2" to="/skills">Skills</router-link>
      <router-link class="nav-link" to="/contact">Contact</router-link>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style lang="postcss">
.nav-link {
  @apply block px-3 py-3 uppercase text-orange-900;
}
.nav-link:hover {
  @apply pb-1 border-b-4 border-orange-700;
}
</style>
