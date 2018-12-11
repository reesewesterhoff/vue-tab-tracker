<template>
  <div>
    <v-layout column>
      <v-flex>
        <panel-component title="Songs">

        </panel-component>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import Panel from '@/components/Panel'

export default {
  components: {
    'panel-component': Panel
  }
}
</script>

<style scoped>
</style>
