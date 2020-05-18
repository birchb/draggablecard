<template>
  <q-card :style="cardStyle" style="max-width: 25vw">
    <q-bar class="bg-primary text-white" v-touch-pan.mouse="onPan">
      <div>Draggable zone</div>
      <q-space></q-space>
      <q-btn dense flat icon="close" @click="closeSelf()"></q-btn>
    </q-bar>

    <q-card-section>{{data}}</q-card-section>
  </q-card>
</template>

<script>
export default {
  name: 'DraggableCard',
  props: ['data'],
  data () {
    return {
      cardPos: {
        x: 0,
        y: 0
      }
    }
  },
  computed: {
    cardStyle () {
      return {
        transform: `translate(${this.cardPos.x}px, ${this.cardPos.y}px)`
      }
    }
  },
  methods: {
    closeSelf () {
      console.log('closeSelf')
      this.$emit('toggleDialogVis')
    },
    onPan (evt) {
      this.cardPos = {
        x: this.cardPos.x + evt.delta.x,
        y: this.cardPos.y + evt.delta.y
      }
    }
  }
}
</script>
