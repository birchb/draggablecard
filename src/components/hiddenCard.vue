<template>
  <q-btn :label="title" @click="showSelf()" class="full-width" />
</template>

<script>
export default {
  name: 'hiddenCard',
  props: ['title', 'visible'],
  data () {
    return {}
  },
  methods: {
    showSelf () {
      this.$emit('update:visible', true)
    },
  }
}
</script>
