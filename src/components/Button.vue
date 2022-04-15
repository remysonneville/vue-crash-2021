<template>
  <button v-on:click="onClick()" :style="{background: color}" class="button">{{text}}</button>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Button',
  props: {
    text: String,
    color: String
  },
  methods: {
    onClick () {
      this.$emit('toggle-add-task')
    }
  }
}
</script>

<style scoped>
</style>
