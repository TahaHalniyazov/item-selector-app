<template>
    <div class="block top-left">
      <h3>Selected Items ({{ items.length }} / 6)</h3>
      <div v-for="it in items" :key="it.id" class="item">
        {{ it.name }}
      </div>
    </div>
  </template>

<script>
export default {
  name: 'TopLeft',
  props: {
    items: Array
  }
}
</script>
