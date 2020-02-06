<template>
  <div class="p-4">

    <h1 class="mb-8 text-3xl font-bold uppercase opacity-50">Resume</h1>

    <article v-for="(job, i) in jobs" :key="i" class="mb-8">
      <panel-card :title="job.title + ' @ ' + job.company" class="p-4">
        <div class="p-4">
          <p>{{job.from}} - {{job.to}}</p>
        </div>
        <section class="mb-4 p-4" v-if="job.overview">
          <h2 class="font-semibold mb-2">Overview</h2>
          <p>{{ job.overview }}</p>
        </section>
        <section class="mb-4 p-4">
          <h2 class="font-semibold mb-2">Experience</h2>
          <ul class="list-disc ml-12">
            <li v-for="(item,i) in job.items" :key="i" class="px-4 py-1">{{item}}</li>
          </ul>
        </section>
        <section class="mb-4 p-4">
          <h2 class="font-semibold mb-2">Accounts / Clients</h2>
          <div class="flex flex-row flex-wrap">
            <div
              v-for="(client, i) in job.highlighted"
              :key="i"
              class="p-4 w-1/4 text-center justify-center"
            >
              <img
                :src="client.logo"
                :alt="client.company"
                class="rounded-lg overflow-hidden mb-4 shadow"
              />
              {{client.company}}
            </div>
          </div>
          <template v-if="job.clients.length">
            <clients-panel>
              <div class="flex flex-row flex-wrap text-center text-xs py-8 bg-gray-100 rounded shadow-inner">
                <div
                  v-for="(client, i) in job.clients"
                  :key="i"
                  class="p-4 w-1/3 justify-center"
                >{{client}}</div>
              </div>
            </clients-panel>
          </template>
        </section>
      </panel-card>
    </article>
  </div>
</template>

<script>
import jobs from "@/data/jobs";
import PanelCard from "@/components/PanelCard";
import ClientsPanel from "@/components/ClientsPanel";
export default {
  name: "resume",
  data() {
    return {
      jobs
    };
  },
  components: {
    PanelCard,
    ClientsPanel
  }
};
</script>
