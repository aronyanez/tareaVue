<template>
  <button @click="enviarEmoji">{{ caracter }}</button>
</template>

<script>
export default {
  props: ['caracter'],
  methods: {
    enviarEmoji () {
      this.$emit('onRecibirEmoji', this.caracter)
    }
  }
}
</script>
