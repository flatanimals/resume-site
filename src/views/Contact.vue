<template>
  <layout>
    <h1>contact me</h1>

    <div class="flex flex-col">
      <skills-list v-for="(set,i) in skillsets" :key="i" :title="set.name" :skills="set.skills" class="w-2/3"></skills-list>
    </div>
  </layout>
</template>

<script>
// @ is an alias to /src
import Layout from './Layout'

export default {
  name: "contact",
  components: {
      Layout
  }

};
</script>
