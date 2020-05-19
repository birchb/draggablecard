<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="toggleCardsVis"></q-btn>
        <div v-if="cardsVis">
          <draggable-card
            :card.sync="card"
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
          data: 1,
          title: "Amy",
          visible: true
        },
        {
          data: 2,
          title: "Billy",
          visible: false
        },
        {
          data: 3,
          title: "Cathleen",
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
