<template>
  <layout>
    <div class="main-content">
      <h1 class="view-header print:text-center">Skills &amp; Technologies</h1>

      <section class="skills">
        <skills-list
          v-for="(set,i) in skillsets"
          :key="i"
          :title="set.name"
          :skills="set.skills"
          class="mb-8 print:mb-0 shadow-lg print:shadow-none"
        ></skills-list>
      </section>
    </div>
  </layout>
</template>

<script>
// @ is an alias to /src
import Layout from "./Layout";
import skillsets from "@/data/skillsets";
import SkillsList from "@/components/SkillsList";

export default {
  name: "home",
  data() {
    return {
      skillsets
    };
  },
  components: {
    Layout,
    SkillsList
  }
};
</script>

<style lang="postcss">
.skills {}
</style>

