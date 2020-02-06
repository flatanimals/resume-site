<template>
  <div>
    <button
      @click="open=!open"
      class="client-panel-toggle hover:bg-gray-100"
    >{{open ? 'Hide': 'Show more'}} Clients</button>
    <div v-if="open">
      <slot></slot>
      <button
        @click="open=false"
        class="client-panel-toggle hover:bg-gray-100"
      >Hide Clients</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "clients-panel",
  data() {
    return {
      open: false
    };
  }
};
</script>

<style lang="postcss">
.client-panel-toggle {
  @apply w-full font-semibold mb-2 text-center mt-2;
  @apply p-4 rounded-lg text-gray-700 ;
}
</style>
