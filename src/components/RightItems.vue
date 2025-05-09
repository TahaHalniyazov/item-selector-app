<template>
    <div class="block bottom-right">
      <h3>Choose One</h3>
      <div
        v-for="it in items"
        :key="it.id"
        :class="['item', { selected: selected && selected.id === it.id }]"
        @click="select(it)"
      >
        {{ it.name }}
      </div>
    </div>
  </template>

<script>
export default {
  name: 'RightItems',
  props: {
    items: Array,
    selected: Object
  },
  emits: ['select'],
  methods: {
    select (item) {
      this.$emit('select', item)
    }
  }
}
</script>
