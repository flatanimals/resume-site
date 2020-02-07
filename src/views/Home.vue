<template>
  <div class="home">
    <div class="home-card" style="max-width:400px">
      <div class="home-card-content">
        <avatar-image src="imgs/1.jpg"></avatar-image>
        <h1 class="home-title md:text-xl lg:text-2xl">FLETCH PADGETT</h1>
        <p class="home-subtitle md:text-base lg:text-lg">Software Developer</p>
        <div class="mt-8">
          <div class="flex justify-around">
            <router-link class="home-link mr-3" to="/resume">Resume</router-link>
            <router-link class="home-link mr-3" to="/skills">Skills</router-link>
            <router-link class="home-link" to="/contact">Contact</router-link>
          </div>
        </div>
      </div>
    </div>
    <div class="home-c">fletch padgett &copy; 2020</div>
  </div>
</template>

<script>
// @ is an alias to /src
import AvatarImage from "@/components/AvatarImage";

export default {
  name: "home",
  data() {
    return {};
  },
  components: {
    AvatarImage
  }
};
</script>

<style lang="postcss">
.home {
  @apply flex;
  @apply flex-col;
  @apply justify-start;
  @apply items-stretch;
  @apply justify-around;
  @apply h-full;
  @apply bg-teal-900;
  @apply p-4;
}

.home-card {
  @apply w-full;
  @apply mx-auto;
  @apply bg-gray-100;
  @apply rounded-t-sm;
  @apply rounded-b;
  @apply overflow-hidden;
  @apply shadow-xl;
}

.home-card-content {
  @apply p-3;
  @apply p-8;
  @apply flex;
  @apply flex-col;
  @apply items-center;
  @apply border-t-4;
  @apply border-orange-500;
}

.home-title {
  @apply mt-4;
  @apply font-semibold;
  @apply text-lg;

  @apply text-gray-800;
}

.home-subtitle {
  @apply text-sm;
  @apply text-gray-600;
}

.home-link {
  @apply block;
  @apply px-3;
  @apply py-2;
  @apply rounded;
  @apply bg-white;
  @apply text-teal-700;
  @apply uppercase;
  @apply text-sm;
  @apply shadow;
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
</style>
