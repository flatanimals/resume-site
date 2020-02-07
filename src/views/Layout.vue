<template>
  <div>
    <header class="site-header print:border-none print:py-4">
      <a
        href="https://github.com/flatanimals/resume-site"
        class="site-header-github"
        target="_blank"
        rel="nofollow"
      >
        <img src="imgs/github-logo.svg" alt="View on Github" />
      </a>
      <h1 class="site-header-title">
        <span class="text-gray-600 border-b print:text-black">fletch</span>
        <span class="print:text-black">er padgett</span>
      </h1>
      <p class="site-header-subtitle">software developer</p>
    </header>
    <site-nav class="site-nav print:hidden"></site-nav>
    <main>
      <slot />
    </main>
    <footer class="site-footer print:hidden">
      <div>Fletch Padgett &copy; 2020</div>
    </footer>
  </div>
</template>

<script>
import SiteNav from "@/components/SiteNav";

export default {
  name: "layout",
  components: {
    SiteNav
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
  @apply relative;
}
.site-header-github {
  @apply absolute;
  @apply top-0;
  @apply right-0;
  @apply w-8;
  @apply h-8;
  @apply mt-3;
  @apply mr-3;
}
.site-header-title {
  @apply mt-4;
  @apply font-semibold;
  @apply text-gray-500;
  @apply text-2xl;
}
.site-header-subtitle {
  @apply text-sm;
  @apply text-gray-500;
  @apply font-light;
}
.site-nav {
  @apply mb-8;
  @apply border-t-2;
  @apply border-orange-700;
  @apply shadow;
}
.site-footer {
  @apply text-gray-600;
  @apply text-sm;
  @apply text-center;
  /* safari hack: safari does not respect bottom margin. */
  @apply pb-8;
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
