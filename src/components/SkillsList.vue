<template>
  <div class="p-4">
      <panel-card :title="title">
      <ul class="px-4">
        <li v-for="(skill,i) in skills" :key="i" class="mb-4">
          <progress-bar :title="skill.label" :max="100" :val="skill.value"></progress-bar>
        </li>
      </ul>
      </panel-card>
  </div>
</template>

<script>
import PanelCard from "./PanelCard";
import ProgressBar from "./ProgressBar";
export default {
  name: "skills-list",
  props: ["title", "skills"],
  components: {
    PanelCard,
    ProgressBar
  }
};
</script>

<style>
</style>
