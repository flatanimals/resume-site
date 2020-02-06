<template>
  <div class="w-full p-4 bg-white border rounded">
    <h2 class="mb-4 font-semibold text-lg">{{title}}</h2>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "panel-card",
  props: ["title"]
};
</script>

<style>
</style>
