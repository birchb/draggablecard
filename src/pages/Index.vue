<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="dialogVis = true"></q-btn>
        <div v-if="dialogVis">
          <draggable-card
            @toggleDialogVis="toggleDataVis"
            v-for="(card, index) in cards"
            :key="index"
          />
        </div>
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
      cards: [
        {
          content: "One"
        },
        {
          content: "Two"
        },
        {
          content: "Three"
        }
      ]
    }
  },
  methods: {
    toggleDataVis () {
      this.dialogVis = !this.dialogVis
    }
  }
}
</script>
