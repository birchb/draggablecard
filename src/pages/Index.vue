<template>
  <q-page>
    <div id="q-app" class="window-height">
      <q-banner inline-actions rounded class="bg-orange text-white">
        Draggable button set layout
        <template v-slot:action>
          <q-btn flat label="Hide" @click="setSplitterModel(100)" v-if="splitterModel < 100" />
          <q-btn flat label="Show" @click="setSplitterModel(80)" v-if="splitterModel === 100" />
        </template>
      </q-banner>
      <q-splitter v-model="splitterModel" class="full-height" :limits="[80, 100]">
        <template v-slot:before>
          <draggable-card v-bind.sync="card" :key="card.id" v-for="card in visibleCards" />
        </template>
        <template v-slot:separator>
          <q-avatar
            v-if="splitterModel < 100"
            color="primary"
            text-color="white"
            size="20px"
            icon="drag_indicator"
          />
        </template>
        <template v-slot:after>
          <hidden-card v-bind.sync="card" :key="card.id" v-for="card in hiddenCards" />
        </template>
      </q-splitter>
    </div>
  </q-page>
</template>

<script>

import DraggableCard from '../components/DraggableCard'
import hiddenCard from '../components/hiddenCard'
export default {
  name: 'PageIndex',
  components: {
    DraggableCard,
    hiddenCard
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
    setSplitterModel (x) {
      this.splitterModel = x
    },
    toggleCardsVis () {
      this.cardsVis = !this.cardsVis
    }
  },
  computed: {
    hiddenCards () {
      return this.cards.filter(card => {
        return !card.visible
      })
    },
    visibleCards () {
      return this.cards.filter(card => {
        return card.visible
      })
    }
  }
}
</script>
