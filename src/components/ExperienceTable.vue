<template>
  <table class="experience-table">
    <thead>
      <tr>
        <th class="experience-table-heading hidden sm:table-cell">Company</th>
        <th class="experience-table-heading">Position</th>
        <th class="experience-table-heading">From</th>
        <th class="experience-table-heading">To</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="exp in experiences"
        :key="exp.company"
        :class="{'bg-yellow-200': hovered == exp.company, 'cursor-pointer': true}"
        @click="naivgateToResumeSection(exp.company)"
        @mouseover="setHover(exp.company)"
        @mouseout="clearHover"
      >
        <td class="px-2 py-2">
          <span class="font-normal">{{exp.company}}</span>
          <span class="sm:hidden">
            <br />
            {{exp.title}}
          </span>
        </td>
        <td class="hidden sm:table-cell px-2 py-2">{{exp.title}}</td>
        <td class="px-2 py-2">{{exp.from.getMonth() +1}}/{{exp.from.getFullYear()}}</td>
        <td class="px-2 py-2">{{exp.to.getMonth() +1}}/{{exp.to.getFullYear()}}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "ExperienceTable",
  props: ["experiences", "hovered"],
  methods: {
    setHover(company) {
      this.$emit("setFocus", company);
    },
    clearHover() {
      this.$emit("setFocus", "");
    },
    naivgateToResumeSection(company) {
      this.$router.push('resume#' + company.toLowerCase().replace(/\s/g,'-'))
    }
  }
};
</script>

<style lang="postcss">
.experience-table {
  @apply text-xs;
  @apply text-blue-900;
  @apply w-full;
  @apply font-light;
}
.experience-table-heading {
  @apply px-2;
  @apply pt-1;
  @apply text-left;
  @apply border-b;
  @apply border-blue-500;
  @apply text-gray-500;
  @apply uppercase;
  @apply font-normal;
}
</style>