<template>
  <div class="home">
    <div class="home-content">
      <h1 class="home-title">
        <span class="text-gray-600 border-b print:text-black">fletch</span>
        <span class="print:text-black">er padgett</span>
      </h1>
      <p class="home-subtitle">software developer</p>
      <div class="mt-8">
        <div class="flex justify-around">
          <router-link class="home-link mr-2" to="/resume">Resume</router-link>
          <router-link class="home-link mr-2" to="/skills">Skills</router-link>
          <router-link class="home-link" to="/contact">Contact</router-link>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {};
  }
};
</script>

<style lang="postcss">
.home {
  @apply flex;
  @apply flex-col;
  @apply justify-start;
  @apply items-stretch;
  @apply h-full;
  @apply bg-gray-100;
  @apply p-4;
  @apply pt-24
}

.home-content {
    @apply text-center;
    @apply mx-auto;
    max-width: 480px;
}

.home-title {
  @apply mt-4;
  @apply font-semibold;
  @apply text-gray-500;
  @apply text-4xl;
}

.home-subtitle {
  @apply text-lg;
  @apply text-gray-500;
  @apply font-light;
}

.home-link {
  @apply block;
  @apply px-3;
  @apply py-2;
  @apply rounded;
  @apply text-teal-700;
  @apply uppercase;
  @apply text-sm;
}

.home-link:hover {
  @apply bg-orange-500;
  @apply text-white;
}

.home-c {
  @apply p-3;
  @apply flex;
  @apply flex-col;
  @apply items-center;
  @apply text-teal-800;
  @apply mx-4 rounded;
}
</style>
