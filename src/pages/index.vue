<template>
  <div class="grid justify-center mt-12 ml-12 mr-12 gap-4">
    <div class="w-100 bg-red-200 p-4 rounded shadow overflow-hidden">
      <h1 class="text-xl font-bold text-pink-900">
        capo
      </h1>
      <nuxt-content v-bind="{ document }" />
    </div>

    <div class="p-4 bg-blue-100">
      <div v-for="{ slug, path } in slugs" :key="path">
        <a class="text-blue-600" :href="path">{{ slug }}</a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  asyncData: async ({ $content }) => {
    const document = await $content('index').fetch()
    const slugs = await $content('posts').only(['slug']).fetch()
    return { document, slugs }
  }
})
</script>
