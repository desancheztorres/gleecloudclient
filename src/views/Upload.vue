<template>
  <div>
    <div class="mb-8">
      Uploader
    </div>
    <div>
      <h2 class="font-medium pb-3 border-b-2 border-gray-100 text-gray-800">Your files</h2>

      <template v-if="files.length">
        <app-file v-for="file in files" :key="file.uuid" :file="file"/>
      </template>

      <p class="mt-3 text-sm text-gray-800" v-else>There are no files here right now</p>

    </div>
  </div>
</template>

<script>

import { mapActions, mapGetters } from 'vuex'
import AppFile from "@/components/AppFile";

export default {
  components: {
    AppFile
  },
  computed: {
    ...mapGetters({
      files: 'files/files'
    })
  },

  methods: {
    ...mapActions({
      getFiles: 'files/getFiles'
    }),
  },

  mounted () {
    this.getFiles()
  }
}
</script>
