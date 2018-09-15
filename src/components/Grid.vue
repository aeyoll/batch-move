<template>
  <div class="grid">
    <div
      v-for="item in sortedItems"
      class="gridItemWrapper"
      :key="item.name">

      <GridItem
        :name="item.name"
        :image="item.image"
        :selected.sync="item.selected"
        :position="item.position"
        ></GridItem>

      <a href="" class="test" v-on:click="moveSelectedAfterItem($event, item)">
        Move here
      </a>
    </div>
  </div>
</template>

<script>
import GridItem from './GridItem'

export default {
  name: 'Grid',

  components: {
    GridItem
  },

  methods: {
    moveSelectedAfterItem: function (event, item) {
      event.preventDefault()
      let position = item.position + 1

      // Shift unselected items
      this.unselectedItemsAfterPosition(position).forEach(item => {
        item.position += this.selectedItems.length
      })

      // Insert selected items in the new location
      this.selectedItems.forEach(selectedItem => {
        selectedItem.position = position
        selectedItem.selected = false
        position++
      })

      // Sort again
      this.items.sort((a, b) => a.position > b.position)

      // Re-calculate the positions so they follow each other
      let min = 1
      this.items.forEach(item => {
        if (item.position > min) {
          item.position = min
        }

        min++
      })
    },

    unselectedItemsAfterPosition: function (position) {
      return this.items.filter(item => item.selected === false && item.position >= position)
    }
  },

  computed: {
    sortedItems: function () {
      return this.items.slice(0).sort((a, b) => a.position > b.position)
    },

    unselectedItems: function () {
      return this.items.filter(item => item.selected === false)
    },

    selectedItems: function () {
      return this.items.filter(item => item.selected === true)
    }
  },
  props: [
    'items'
  ]
}
</script>

<style scope>
  .grid {
    display: flex;
    flex-wrap: wrap;
  }

  .gridItemWrapper {
    align-items: center;
    display: flex;
    margin-bottom: 10px;
    margin-right: 50px;
  }
</style>
