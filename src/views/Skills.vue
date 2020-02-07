<template>
  <layout>
    <div class="main-content">
      <h1 class="view-header print:text-center">Skills &amp; Technologies</h1>

      <div class="pb-8">
        <skills-list
          v-for="(set,i) in skillsets"
          :key="i"
          :title="set.name"
          :skills="set.skills"
          class="mb-8 shadow-lg print:shadow-none print:mb-0"
        ></skills-list>
      </div>
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
