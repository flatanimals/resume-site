<template>
  <nav class="nav-bar">
    <div class="flex justify-around">
      <router-link class="nav-link" to="/">Home</router-link>
      <router-link class="nav-link" to="/resume">Resume</router-link>
      <router-link class="nav-link" to="/skills">Skills</router-link>
      <router-link class="nav-link" to="/contact">Contact</router-link>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style lang="postcss">
.nav-bar {
  @apply flex;
  @apply justify-center;
  @apply w-full;
  @apply bg-orange-500;
  @apply border-b;
  @apply border-orange-700;
}
.nav-link {
  @apply block px-3 py-3 uppercase text-orange-900 mr-2;
}
.nav-link:hover,
.nav-link.router-link-exact-active {
  @apply pb-1 border-b-4 border-orange-700;
}
.nav-link:last-child {
    @apply mr-0;
}
</style>
