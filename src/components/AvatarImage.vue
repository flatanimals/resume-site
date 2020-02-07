<template>
  <div class="avatar w-32 h-32 md:w-40 md:h-40 lg:w-48 lg:h-48">
    <img :src="src" alt="Image" class />
  </div>
</template>

<script>
export default {
    name: 'avatar-image',
    props: ['src']
};
</script>

<style lang="postcss">
.avatar {
  @apply bg-gray-700;
  @apply rounded-full;
  @apply flex flex-col;
  @apply items-center;
  @apply justify-center;
  @apply overflow-hidden;
  @apply shadow-lg;
}
</style>
