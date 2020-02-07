<template>
  <router-view />
</template>

<script>

export default {
  name: "main-app",
};
</script>

<style lang="postcss">
@import "assets/styles/tailwind.postcss";

html,
body {
  @apply bg-gray-200;
  @apply h-full;
}

#app {
  @apply h-full;
}
</style>
