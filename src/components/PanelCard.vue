<template>
  <div class="panel-card">
    <h2 class="panel-card-title">{{title}}</h2>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "panel-card",
  props: ["title"]
};
</script>

<style lang="postcss">
.panel-card {
  @apply w-full;
  @apply p-4;
}
.panel-card-title {
  @apply mb-4;
  @apply font-semibold;
  @apply text-lg;
}
</style>
