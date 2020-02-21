<template>
  <div class="home">
    <div class="home-content">
      <h1 class="home-title">
        <span class="text-gray-600 border-b print:text-black">fletch</span>
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
    <div class="home-clients">
      <div class="home-clients-heading">Past Clients</div>
      <div class="home-client-list md:p-4 md:w-4/5 lg:3/5 m-auto">
        <div v-for="(client, i) in clients" :key="i" class="p-4 w-1/4 sm:w-1/6">
          <img
            :src="client.logo"
            :alt="client.company"
            :title="client.company"
            class="home-client-image"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import jobs from "@/data/jobs";
export default {
  name: "home",
  data() {
    return {
      jobs
    };
  },
  computed: {
    clients() {
      return [].concat(...jobs.map(x => x.highlighted));
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
  @apply bg-gray-100;
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
  @apply px-3;
  @apply py-2;
  @apply rounded;
  @apply text-teal-700;
  @apply uppercase;
  @apply text-sm;
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
  @apply text-teal-800;
  @apply mx-4 rounded;
}
.home-clients {
  @apply px-4;
  @apply py-16;
  @apply bg-teal-900;
}
.home-clients-heading {
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
.home-client-list {
  @apply flex;
  @apply flex-row;
  @apply flex-wrap;
  @apply justify-center;
}
.home-client-image {
  @apply rounded-lg;
  @apply overflow-hidden;
  @apply mb-4;
  @apply shadow;
  filter: grayscale(100%);
}
.home-client-image:hover {
  filter: none;
}
</style>
