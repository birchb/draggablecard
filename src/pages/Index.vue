<template>
  <q-page class="flex flex-center">
    <div id="q-app">
      <div class="q-pa-md q-gutter-sm">
        <q-btn label="Draggable Card" color="primary" @click="dialogVis = true"></q-btn>

        <q-card :style="cardStyle" v-if="dialogVis" style="max-width: 25vw">
          <q-bar class="bg-primary text-white" v-touch-pan.mouse="onPan">
            <div>Draggable zone</div>
            <q-space></q-space>
            <q-btn dense flat icon="close" @click="dialogVis = false"></q-btn>
          </q-bar>

          <q-card-section>
            <div>Dialog content 1</div>
            <div>Dialog content 2</div>
            <div>Dialog content 3</div>
            <div>Dialog content 4</div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      dialogVis: false,
      cardPos: {
        x: 0,
        y: 0
      }
    }
  },
  computed: {
    cardStyle() {
      return {
        transform: `translate(${this.cardPos.x}px, ${this.cardPos.y}px)`
      }
    }
  },
  methods: {
    onPan(evt) {
      this.cardPos = {
        x: this.cardPos.x + evt.delta.x,
        y: this.cardPos.y + evt.delta.y
      }
    }
  }
}
</script>
