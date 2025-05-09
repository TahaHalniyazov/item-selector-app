<template>
    <div class="block bottom-left">
      <h3>Your Items</h3>
      <div
        v-for="it in items"
        :key="it.id"
        :class="['item', { selected: selected.some(s => s.id === it.id) }]"
        @click="toggle(it)"
      >
        {{ it.name }}
      </div>
      <div class="info">selected: {{ selected.length }} / 6</div>
    </div>
  </template>

<script>
export default {
  name: 'LeftItems',
  props: {
    items: Array,
    selected: Array
  },
  emits: ['toggle'],
  methods: {
    toggle (item) {
      this.$emit('toggle', item)
    }
  }
}
</script>
