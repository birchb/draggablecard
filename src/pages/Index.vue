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
            :data="card.data"
            v-show="card.visible"
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
          data: "One",
          visible: true
        },
        {
          data: "Two",
          visible: false
        },
        {
          data: "Three",
          visible: true
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
