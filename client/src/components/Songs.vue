<template>
  <div>
    <v-layout column>
      <v-flex>
        <panel-component title="Songs">
          <div v-for="song in songs" :key="song.title">
            {{song.title}}
            {{song.artist}}
            {{song.album}}
          </div>
        </panel-component>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import Panel from '@/components/Panel'
import SongsService from '@/services/SongsService'

export default {
  components: {
    'panel-component': Panel
  },
  data () {
    return {
      songs: null
    }
  },
  async mounted () {
    // request for all songs on back end
    this.songs = await SongsService.getAllSongs()
  }
}
</script>

<style scoped>
</style>
