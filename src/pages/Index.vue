<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="dialogVis = true"></q-btn>
        <draggable-card v-if="dialogVis" @toggleDialogVis="toggleDataVis" />
      </div>
    </div>
  </q-page>
</template>

<script>

import DraggableCard from '../components/DraggableCard'
export default {
  name: 'PageIndex',
  components: {
    DraggableCard
  },
  data () {
    return {
      dialogVis: false,
    }
  },
  methods: {
    toggleDataVis () {
      this.dialogVis = !this.dialogVis
    }
  }
}
</script>
