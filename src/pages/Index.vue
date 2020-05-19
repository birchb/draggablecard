<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="toggleCardsVis"></q-btn>
        <div v-if="cardsVis">
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
      cardsVis: false,
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
    toggleCardsVis () {
      this.cardsVis = !this.cardsVis
    }
  }
}
</script>
