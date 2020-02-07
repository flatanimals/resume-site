<template>
  <div class="mx-auto">
    <panel-card :title="title" class="bg-white print:ml-16">
      <ul class="skills-list">
        <li
          v-for="(skill,i) in skills"
          :key="i"
          class="mb-2 w-1/2 md:w-1/4 print:w-1/3 print:mb-0"
        >{{ skill.label }}</li>
      </ul>
    </panel-card>
  </div>
</template>

<script>
import PanelCard from "./PanelCard";
export default {
  name: "skills-list",
  props: ["title", "skills"],
  components: {
    PanelCard
  }
};
</script>

<style lang="postcss">
.skills-list {
  @apply ml-4;
  @apply p-2;
  @apply flex;
  @apply flex-wrap;
  @apply list-disc;
}
</style>
