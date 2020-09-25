<template>
  <div id="list">
    <div v-for="(item, i) in thingsToDo" v-bind:key="item">
      {{i + 1}}) {{item}}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
        name: 'List',
        thingsToDo: ['Lavar a louça', 'Varrer a casa']      
    }
  }
}
</script>

<style scoped>
</style>
