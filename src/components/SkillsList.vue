<template>
  <div class="">
      <panel-card :title="title" class="bg-white">
      <ul class="ml-4 p-2 flex flex-wrap list-disc">
        <li v-for="(skill,i) in skills" :key="i" class="mb-4 w-1/2 md:w-1/4">{{ skill.label }}</li>
      </ul>
      </panel-card>
  </div>
</template>

<script>
import PanelCard from "./PanelCard";
// import ProgressBar from "./ProgressBar";
export default {
  name: "skills-list",
  props: ["title", "skills"],
  components: {
    PanelCard,
    // ProgressBar
  }
};
</script>

<style>
</style>
