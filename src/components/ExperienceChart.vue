<template>
  <div>
    <div class="experience-chart">
      <div class="absolute inset-0 z-0">
        <div
          v-for="n in years"
          :key="n"
          class="experience-chart-vbar"
          :style="verticalBarStyles(n)"
        ></div>
      </div>
      <div v-for="exp in experienceBars" :key="exp.company" class="py-1 border-b border-blue-300">
        <div class="relative h-4 sm:h-6" @mouseover="setHover(exp.company)" @mouseout="clearHover">
          <div
            class="experience-chart-hbar"
            :style="expBarStyles(exp)"
            :class="{'bg-green-500': hovered == exp.company,  'bg-blue-500': hovered != exp.company}"
          ></div>
        </div>
      </div>
    </div>
    <div class="flex flex-row justify-between text-blue-900 text-xs mb-5">
      <span>{{ minYear }}</span>
      <span>{{ (new Date()).getFullYear() }}</span>
    </div>
  </div>
</template>

<script>
const diffMonths = (from, to) => {
  return (
    (to.getFullYear() - from.getFullYear()) * 12 +
    (to.getMonth() - from.getMonth())
  );
};

export default {
  name: "experience-chart",
  props: ["experiences", "hovered"],
  computed: {
    minYear() {
      return Math.min(...this.experiences.map(x => x.from.getFullYear()));
    },
    maxYear() {
      return Math.max(...this.experiences.map(x => x.to.getFullYear()));
    },
    startingDate() {
      return new Date(this.minYear, 0);
    },
    totalMonths() {
      var now = new Date();
      return (now.getFullYear() - this.minYear) * 12 + now.getMonth();
    },
    years() {
      var now = new Date();
      return now.getFullYear() - this.minYear;
    },
    experienceBars() {
      return this.experiences.map(({ company, to, from, title }) => {
        return {
          company,
          from,
          to,
          title,
          months: diffMonths(from, to),
          offset: diffMonths(this.startingDate, from)
        };
      });
    }
  },
  methods: {
    expBarStyles({ months, offset }) {
      return {
        width: (months / this.totalMonths) * 100 + "%",
        left: (offset / this.totalMonths) * 100 + "%"
      };
    },
    verticalBarStyles(offset) {
      const baseOffset = (12 / this.totalMonths) * 100;
      return {
        left: offset * baseOffset + "%"
      };
    },
    setHover(company) {
      this.$emit("setFocus", company);
    },
    clearHover() {
      this.$emit("setFocus", "");
    }
  }
};
</script>

<style lang="postcss">
.experience-chart {
  @apply border;
  @apply border-blue-300;
  @apply bg-blue-100;
  @apply shadow-inner;
  @apply relative;
  @apply rounded-sm;
}
.experience-chart-vbar {
  @apply absolute;
  @apply top-0;
  @apply bottom-0;
  @apply w-px;
  @apply bg-blue-300;
}
.experience-chart-hbar {
  @apply h-4;
  @apply absolute;
  @apply border-b;
  @apply border-r;
  @apply border-blue-900;
  @apply opacity-90;
  @apply rounded-sm;
}
@screen sm {
  .experience-chart-hbar {
    @apply h-6;
  }
}
</style>