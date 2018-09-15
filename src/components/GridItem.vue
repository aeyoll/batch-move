<template>
  <div class="gridItem" v-bind:class="{ selected: selected }">
    <div class="gridItemContent" v-on:click="toggle()">
      <div>
        <img :src="image" :alt="name">
      </div>

      <div>
        {{ name }}
        {{ position }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GridItem',
  methods: {
    toggle: function () {
      this.$emit('update:selected', !this.selected)
    }
  },
  props: [
    'name',
    'image',
    'selected',
    'position'
  ]
}
</script>

<style scoped>
  .gridItem {
    border: 2px solid black;
    margin-right: 10px;
    text-align: center;
  }

  .gridItemContent {
    cursor: pointer;
  }

  .gridItem.selected {
    border: 2px solid red;
  }
</style>
