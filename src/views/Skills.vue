<template>
  <div class>
    <h1 class="px-4 text-lg font-bold">Skills</h1>

    <div class="flex flex-col">
      <skills-list v-for="(set,i) in skillsets" :key="i" :title="set.name" :skills="set.skills" class="w-2/3"></skills-list>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import skillsets from '@/data/skillsets'
import SkillsList from "@/components/SkillsList";

export default {
  name: "home",
  data() {
    return {
      skillsets
    };
  },
  components: {
    SkillsList
  }
};
</script>
