<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="dialogVis = true"></q-btn>
        <div v-if="dialogVis">
          <draggable-card
            :data="card.data"
            :index="index"
            :key="index"
            @hideCard="hideCard"
            v-for="(card, index) in cards"
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
    hideCard (index) {
      console.log('hideCard -> index', index)
      this.cards[index].visible = false
    },
    toggleDataVis () {
      this.dialogVis = !this.dialogVis
    }
  }
}
</script>
