<template>
    <div class="block top-right">
      <h3>Selected Item</h3>
      <div v-if="item" class="item">
        {{ item.name }}
      </div>
    </div>
  </template>

<script>
export default {
  name: 'TopRight',
  props: {
    item: Object
  }
}
</script>
