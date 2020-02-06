<template>
  <div id="app" class="py-8 md:flex">
    <div class="flex-shrink-0 md:w-64">
      <header class="m-4 p-3 flex flex-col items-center">
        <div class="kennyg">
          <img src="imgs/me.jpg" alt="F" class />
        </div>
        <h1 class="mt-4 font-semibold text-grey-800">FLETCH PADGETT</h1>
        <p class="text-sm text-gray-600">Software Developer</p>
        <div class="mt-8">
          <a href class="block px-3 py-2 rounded text-gray-900 uppercase text-sm border">Resume</a>
        </div>
      </header>
    </div>
    <div class="w-full">
    <site-nav></site-nav>
      <main class="m-4 bg-wite rounded-lg">
        <router-view />
      </main>
      <footer class="bg-gray-90 text-gray-600 m-4 p-3 rounded-lg flex justify-between text-sm">
        <div>Fletch Padgett</div>
        <div>&copy; 2020</div>
      </footer>
    </div>
  </div>
</template>

<script>
import SiteNav from "@/components/SiteNav";

export default {
    name: 'main-app',
    components: {
        SiteNav
    }
};
</script>

<style lang="postcss">
@import "assets/styles/tailwind.postcss";

html,
body {
  @apply bg-gray-200;
}

/* body {
      background-image: linear-gradient(transparent, rgba(33,33,33,0.25));
} */

.kennyg {
  @apply w-32 h-32 bg-blue-700 rounded-full flex flex-col items-center justify-center overflow-hidden shadow;
}
</style>
