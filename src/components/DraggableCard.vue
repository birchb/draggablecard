<template>
  <q-card :style="cardStyle" style="max-width: 20vw">
    <q-bar class="bg-primary text-white" v-touch-pan.mouse="onPan">
      <div>{{title}}</div>
      <q-space></q-space>
      <q-btn dense flat icon="close" @click="closeSelf()"></q-btn>
    </q-bar>

    <q-card-section>Data: {{data}}</q-card-section>
    <q-btn-group spread>
      <q-btn outline color="brown" label="-" @click="decrement" />
      <q-btn outline color="brown" label="+" @click="increment" />
    </q-btn-group>
  </q-card>
</template>

<script>
export default {
  name: 'DraggableCard',
  props: ['data', 'title', 'visible'],
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
      // this.$emit('hideCard', this.index)
      this.$emit('update:visible', false)
    },
    decrement () {
      this.$emit('update:data', this.data - 1)
    },
    increment () {
      this.$emit('update:data', this.data + 1)
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
