<template>
  <layout>
    <div class="main-content">
      <h1 class="view-header">Resume</h1>

      <article v-for="(job, i) in jobs" :key="i" class="resume">
        <panel-card>
          <div class="text-center">
            <p class="text-4xl mb-4">{{job.company}}</p>
            <p class="text-lg">{{job.title}}</p>
            <p class="text-sm text-gray-700 mb-2">{{job.from}} - {{job.to}}</p>
          </div>
          <section class="mb-4" v-if="job.overview">
            <h2 class="resume-section-header">Overview</h2>
            <p>{{ job.overview }}</p>
          </section>
          <section class="mb-4 py-4 md:px-16">
            <!-- <h2 class="resume-section-header">Experience</h2> -->
            <ul class="list-disc ml-6">
              <li v-for="(item,i) in job.items" :key="i" class="py-1">{{item}}</li>
            </ul>
          </section>
          <section class="mb-4">
            <h2 class="resume-section-header">Accounts / Clients</h2>
            <div class="flex flex-row flex-wrap md:p-4">
              <div
                v-for="(client, i) in job.highlighted"
                :key="i"
                class="p-4 w-1/2 sm:w-1/4 text-center justify-center"
              >
                <img
                  :src="client.logo"
                  :alt="client.company"
                  class="rounded-lg overflow-hidden mb-4"
                />
                <div class="text-sm hidden">{{client.company}}</div>
              </div>
            </div>
          </section>
          <section v-if="job.visuals.length" class="md:p-8">
            <div v-for="(visual,i) in job.visuals" :key="i">
              <div class="rounded-lg overflow-hidden my-2">
                <img :src="visual.src" :alt="visual.caption" />
              </div>
              <p class="text-sm italic pl-2 mb-0">{{visual.caption}}</p>
            </div>
          </section>
        </panel-card>
      </article>
    </div>
  </layout>
</template>

<script>
import jobs from "@/data/jobs";
import Layout from "./Layout";
import PanelCard from "@/components/PanelCard";
export default {
  name: "resume",
  data() {
    return {
      jobs
    };
  },
  components: {
    Layout,
    PanelCard
  }
};
</script>


<style lang="postcss">
.resume {
  @apply mb-8;
  @apply mx-auto;
  @apply px-2;
  @apply bg-white;
  @apply shadow-lg
}

.resume-section-header {
  @apply text-xl;
  @apply font-semibold;
  @apply text-center;
  @apply mb-8;
}
</style>
