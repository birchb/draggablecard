<template>
  <q-page>
    <div id="q-app" class="window-height">
      <!-- <div class="q-pa-md q-gutter-sm full-height"> -->
      <q-splitter v-model="splitterModel" class="full-height">
        <template v-slot:before>
          <draggable-card
            v-bind.sync="card"
            :key="card.id"
            v-for="card in cards"
            v-show="card.visible"
          />
        </template>
        <template v-slot:separator>
          <q-avatar color="primary" text-color="white" size="40px" icon="drag_indicator" />
        </template>
        <template v-slot:after></template>
      </q-splitter>
    </div>
    <!-- </div> -->
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
      ],
      splitterModel: 80
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
