<template>
  <div class="container">
    <div class="area blocks-top">
      <TopLeft :items="selectedLeft" />
      <TopRight :item="selectedRight" />
    </div>
    <div class="area blocks-bottom">
      <LeftItems
        :items="leftItems"
        :selected="selectedLeft"
        @toggle="toggleLeft"
      />
      <RightItems
        :items="rightItems"
        :selected="selectedRight"
        @select="selectRight"
      />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import LeftItems from './components/LeftItems.vue'
import RightItems from './components/RightItems.vue'
import TopLeft from './components/TopLeft.vue'
import TopRight from './components/TopRight.vue'

export default {
  name: 'App',
  components: { LeftItems, RightItems, TopLeft, TopRight },
  setup () {
    const leftItems = [
      { id: 1, name: 'Shoes 1' },
      { id: 2, name: 'Shoes 2' },
      { id: 3, name: 'Shoes 3' },
      { id: 4, name: 'Shoes 4' },
      { id: 5, name: 'T-shirt 1' },
      { id: 6, name: 'T-shirt 2' },
      { id: 7, name: 'T-shirt 3' },
      { id: 8, name: 'T-shirt 4' }
    ]
    const rightItems = [
      { id: 11, name: 'Jacket 1' },
      { id: 12, name: 'Jacket 2' },
      { id: 13, name: 'Jacket 3' },
      { id: 14, name: 'Jacket 4' },
      { id: 15, name: 'Hoodie 1' },
      { id: 16, name: 'Hoodie 2' },
      { id: 17, name: 'Hoodie 3' },
      { id: 18, name: 'Hoodie 4' }
    ]

    const selectedLeft = ref([])
    const selectedRight = ref(null)

    function toggleLeft (item) {
      const idx = selectedLeft.value.findIndex(i => i.id === item.id)
      if (idx !== -1) {
        selectedLeft.value.splice(idx, 1)
      } else if (selectedLeft.value.length < 6) {
        selectedLeft.value.push(item)
      }
    }

    function selectRight (item) {
      if (selectedRight.value && selectedRight.value.id === item.id) {
        selectedRight.value = null
      } else {
        selectedRight.value = item
      }
    }

    return {
      leftItems,
      rightItems,
      selectedLeft,
      selectedRight,
      toggleLeft,
      selectRight
    }
  }
}
</script>
