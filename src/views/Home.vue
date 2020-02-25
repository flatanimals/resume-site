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
        <div class="border border-blue-300 bg-blue-100 shadow-inner relative rounded-sm">
          <div class="absolute inset-0 z-0">
            <div
              v-for="n in years"
              :key="n"
              class="absolute top-0 bottom-0 w-px bg-blue-300"
              :style="verticalBarStyles(n)"
            ></div>
          </div>
          <div v-for="exp in experiences" :key="exp.company" class="py-1 border-b border-blue-300">
            <div
              class="relative h-4 sm:h-6"
              @mouseover="setHover(exp.company)"
              @mouseout="clearHover"
            >
              <div
                class="h-4 sm:h-6 absolute border-b border-r border-blue-900 opacity-90 rounded-sm"
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

        <div>
          <table class="text-xs text-blue-900 w-full font-light">
            <thead>
              <tr>
                <th
                  class="hidden sm:table-cell px-2 pt-1 text-left border-b border-blue-500 text-gray-500 uppercase font-normal"
                >Company</th>
                <th
                  class="px-2 pt-1 text-left border-b border-blue-500 text-gray-500 uppercase font-normal"
                >Postion</th>
                <th
                  class="px-2 pt-1 text-left border-b border-blue-500 text-gray-500 uppercase font-normal"
                >From</th>
                <th
                  class="px-2 pt-1 text-left border-b border-blue-500 text-gray-500 uppercase font-normal"
                >To</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="exp in experiences"
                :key="exp.company"
                :class="{'bg-yellow-200': hovered == exp.company}"
                @mouseover="setHover(exp.company)"
                @mouseout="clearHover"
              >
                <td class="px-2 py-2">
                  <router-link :to="'resume#' + exp.company.toLowerCase().replace(/\s/g,'-')">
                    <span class="font-normal">{{exp.company}}</span>
                    <span class="sm:hidden">
                      <br />
                      {{exp.title}}
                    </span>
                  </router-link>
                </td>
                <td class="hidden sm:table-cell px-2 py-2">{{exp.title}}</td>
                <td class="px-2 py-2">{{exp.from.getMonth() +1}}/{{exp.from.getFullYear()}}</td>
                <td class="px-2 py-2">{{exp.to.getMonth() +1}}/{{exp.to.getFullYear()}}</td>
              </tr>
            </tbody>
          </table>
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

const prepDate = input => {
  var [month, year] = input.split("/");
  return new Date(year, month - 1);
};
const diffMonths = (from, to) => {
  return (
    (to.getFullYear() - from.getFullYear()) * 12 +
    (to.getMonth() - from.getMonth())
  );
};

export default {
  name: "home",
  data() {
    return {
      hovered: ""
    };
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
            months: diffMonths(from, to),
            offset: diffMonths(this.startingDate, from)
          };
        })
        .sort((a, b) => (a.to < b.to ? 1 : -1));
    },
    minYear() {
      return Math.min(...jobs.map(x => prepDate(x.from).getFullYear()));
    },
    maxYear() {
      return Math.max(...jobs.map(x => prepDate(x.to).getFullYear()));
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
      console.log(company);
      this.hovered = company;
    },
    clearHover() {
      this.hovered = "";
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
