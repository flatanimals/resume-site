<template>
  <div>
    <header class="site-header">
      <!-- <AvatarImage src="imgs/me.jpg" class="w-32 h-32"></AvatarImage> -->
      <h1 class="site-header-title">
        <span class="text-gray-600 border-b">fletch</span>
        <span class="text-gray-500">er padgett</span>
      </h1>
      <p class="site-header-subtitle">software developer</p>
    </header>
    <site-nav class="mb-8 border-t-2 border-orange-700"></site-nav>
    <main>
      <slot />
    </main>
    <footer class="text-gray-600 text-sm text-center mb-8">
      <div>Fletch Padgett &copy; 2020</div>
    </footer>
  </div>
</template>

<script>
// import AvatarImage from "@/components/AvatarImage";
import SiteNav from "@/components/SiteNav";

export default {
  name: "layout",
  components: {
    SiteNav
    // AvatarImage
  }
};
</script>

<style lang="postcss">
.site-header {
  @apply text-center;
  @apply py-8;
  @apply border-b-8;
  @apply border-teal-900;
  @apply bg-white;
}
.site-header-title {
  @apply mt-4;
  @apply font-semibold;
  /* @apply text-gray-100; */
  @apply text-2xl;
}
.site-header-subtitle {
  @apply text-sm;
  @apply text-gray-500;
  @apply font-light;
}

.main-content {
  @apply mx-auto;
  max-width: 800px;
}
.view-header {
  @apply mx-4;
  @apply font-bold;
  @apply text-xl;
  @apply uppercase;
  @apply leading-none;
  @apply opacity-50;
  @apply pb-6;
  letter-spacing: 1px;
}
</style>
