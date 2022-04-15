<template>
  <header>
    <h1>{{title}}</h1>
    <Button @toggle-add-task="$emit('toggle-add-task')" text="Ajouter" color="black" />
  </header>

</template>

<script>
import Button from '@/components/Button'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Header',
  props: {
    title: String
  },
  components: {
    Button
  }
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
