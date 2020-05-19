<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="toggleCardsVis"></q-btn>
        <div v-if="cardsVis">
          <draggable-card
            v-bind.sync="card"
            :key="card.id"
            v-for="card in cards"
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
          id: 1,
          title: "Amy",
          visible: true
        },
        {
          data: 2,
          id: 2,
          title: "Billy",
          visible: false
        },
        {
          data: 3,
          id: 3,
          title: "Cathleen",
          visible: true
        }
      ]
    }
  },
  methods: {
    // hideCard (index) {
    //   console.log('hideCard -> index', index)
    //   this.cards[index].visible = false
    // },
    toggleCardsVis () {
      this.cardsVis = !this.cardsVis
    }
  }
}
</script>
