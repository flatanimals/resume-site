<template>
  <layout>
    <div class="main-content">
      <h1 class="view-header print:hidden">Resume</h1>

      <article
        v-for="(job, i) in jobs"
        :key="i"
        class="resume shadow-lg print:shadow-none mb-8 print:mb-0"
      >
        <panel-card>
          <div class="text-center">
            <p class="text-4xl mb-4">{{job.company}}</p>
            <p class="text-lg">{{job.title}}</p>
            <p class="text-sm text-gray-700 mb-2">{{job.from}} - {{job.to}}</p>
          </div>
          <section class="mb-4" v-if="job.overview">
            <p>{{ job.overview }}</p>
          </section>
          <section class="mb-4 py-4 md:px-16">
            <ul class="list-disc ml-6">
              <li v-for="(item,i) in job.items" :key="i" class="py-1 print:leading-tight">{{item}}</li>
            </ul>
          </section>
          <section class="mb-4 print:hidden">
            <h2 class="resume-section-header">Accounts / Clients</h2>
            <div class="resume-client-list md:p-4">
              <div
                v-for="(client, i) in job.highlighted"
                :key="i"
                class="p-4 w-1/2 sm:w-1/4 print:w-1/4"
              >
                <img
                  :src="client.logo"
                  :alt="client.company"
                  :title="client.company"
                  class="resume-client-image"
                />
              </div>
            </div>
          </section>
          <section v-if="job.visuals.length" class="md:p-8 print:hidden">
            <div v-for="(visual,i) in job.visuals" :key="i">
              <div class="resume-visual">
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
  @apply mx-auto;
  @apply px-2;
  @apply bg-white;
  page-break-after: always;
}

.resume:last-of-type {
  page-break-after: avoid;
}

.resume-section-header {
  @apply text-xl;
  @apply font-semibold;
  @apply text-center;
  @apply mb-8;
}
.resume-client-list {
  @apply flex;
  @apply flex-row;
  @apply flex-wrap;
  @apply justify-center;
}
.resume-client-image {
  @apply rounded-lg;
  @apply overflow-hidden;
  @apply mb-4;
}
.resume-visual {
  @apply rounded-lg;
  @apply overflow-hidden;
  @apply my-2;
}
</style>
