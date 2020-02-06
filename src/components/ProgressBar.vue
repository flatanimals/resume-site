<template>
  <div>
    <div v-if="title" class="px-1 mb-2">{{title}}</div>
    <div class=" bg-gray-300 w-full h-2 rounded-full shadow shadow-inner overflow-hidden">
      <div class="h-full bg-teal-600  rounded-full" :style="barWidth"></div>
    </div>
    <div class="flex justify-between text-xs mt-1 px-2 text-gray-500">
        <span>Noob</span>
        <span>Beginner</span>
        <span>Intermediate</span>
        <span>Advanced</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "progress-bar",
  props: ["title", "max", "val"],
  computed: {
    barWidth() {
      var iMax = parseInt(this.max);
      var iVal = parseInt(this.val);
      var iPercent = Math.ceil((iVal / iMax) * 100);
      return { width: iPercent + "%" };
    }
  }
};
</script>

<style>
</style>
