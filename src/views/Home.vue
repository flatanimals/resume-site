<template>
  <div class="home">
    <div class="home-content">
      <h1 class="home-title">
        <span class="text-blue-600 border-b print:text-black">fletch</span>
        <span class="print:text-black">er padgett</span>
      </h1>
      <p class="home-subtitle">software developer</p>
      <div class="my-8">
        <div class="flex justify-around">
          <router-link class="home-link mr-2" to="/resume">Resume</router-link>
          <router-link class="home-link mr-2" to="/skills">Skills</router-link>
          <router-link class="home-link" to="/contact">Contact</router-link>
        </div>
      </div>
    </div>
    <div class="home-timeline px-4 py-8 sm:py-16">
      <div class="home-heading">Work Experience</div>
      <div class="w-full sm:w-4/5 p-4 my-4 sm:my-8 mx-auto bg-white border shadow-xl rounded-sm">
        <experience-chart
          :experiences="experiences"
          :hovered="hovered"
          @setFocus="handleSetFocus"
        />

        <div>
          <experience-table
            :experiences="experiences"
            :hovered="hovered"
            @setFocus="handleSetFocus"
          />
        </div>
      </div>
    </div>
    <div class="home-clients">
      <div class="home-heading">Past Clients</div>
      <div class="home-client-list md:p-4 md:w-4/5 lg:3/5 m-auto">
        <div v-for="(client, i) in clients" :key="i" class="p-4 w-1/3 sm:w-1/6">
          <img
            :src="client.logo"
            :alt="client.company"
            :title="client.company"
            class="home-client-image"
          />
        </div>
        <div class="p-4 w-1/3 sm:w-1/6">
          <router-link to="/contact" class="home-client-image block">
            <svg
              class="w-full bg-blue-800 fill-current text-blue-600 hover:bg-orange-500 hover:text-white"
              viewBox="0 0 16 16"
            >
              <rect x="4" y="7" width="8" height="2" />
              <rect x="7" y="4" width="2" height="8" />
            </svg>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import jobs from "@/data/jobs";
import ExperienceChart from "@/components/ExperienceChart.vue";
import ExperienceTable from "@/components/ExperienceTable.vue";

const prepDate = input => {
  var [month, year] = input.split("/");
  return new Date(year, month - 1);
};


export default {
  name: "home",
  data() {
    return {
      hovered: ""
    };
  },
  components: {
    ExperienceChart,
    ExperienceTable
  },
  computed: {

    clients() {
      return [].concat(...jobs.map(x => x.highlighted));
    },
    experiences() {
      return jobs
        .map(({ company, to, from, title }) => {
          from = prepDate(from);
          to = prepDate(to);
          return {
            company,
            from,
            to,
            title,
          };
        })
        .sort((a, b) => (a.to < b.to ? 1 : -1));
    }
  },
  methods: {
    handleSetFocus(value) {
      this.hovered = value;
    }
  }
};
</script>

<style lang="postcss">
.home {
  @apply flex;
  @apply flex-col;
  @apply justify-start;
  @apply items-stretch;
  @apply bg-orange-100;
  @apply pt-24;
}

.home-content {
  @apply text-center;
  @apply mx-auto;
  @apply px-4;
  max-width: 480px;
}

.home-title {
  @apply mt-4;
  @apply font-semibold;
  @apply text-gray-500;
  @apply text-4xl;
}

.home-subtitle {
  @apply text-lg;
  @apply text-gray-500;
  @apply font-light;
}

.home-link {
  @apply block;
  @apply mx-2;
  @apply px-3;
  @apply py-1;
  @apply rounded;
  @apply text-blue-600;
  @apply uppercase;
}

.home-link:hover {
  @apply bg-orange-500;
  @apply text-white;
}

.home-c {
  @apply p-3;
  @apply flex;
  @apply flex-col;
  @apply items-center;
  @apply text-blue-800;
  @apply mx-4 rounded;
}
.home-heading {
  @apply text-center;
  @apply mx-4;
  @apply font-bold;
  @apply text-xl;
  @apply uppercase;
  @apply leading-none;
  @apply opacity-50;
  @apply pb-6;
  letter-spacing: 1px;
}
.home-clients {
  @apply px-4;
  @apply py-16;
  @apply bg-blue-600;
  @apply border-t-8;
  @apply border-blue-600;
}

.home-client-list {
  @apply flex;
  @apply flex-row;
  @apply flex-wrap;
  @apply justify-start;
}
.home-client-image {
  @apply rounded;
  @apply overflow-hidden;
  @apply mb-4;
  @apply shadow;
}
</style>
