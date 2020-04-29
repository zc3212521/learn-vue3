<template>
  <h3>This is children</h3>
  <div>
    <button @click="() => {changeComponent('reactive&ref')}">reactive & ref 用法</button>
    <button @click="() => {changeComponent('ref')}">ref 引用</button>
    <button @click="() => {changeComponent('watch')}">watch</button>
  </div>
  ---{{ showComponent }}---
  <reactive-and-ref v-if="showComponent === 'reactive&ref'" />
  <watch v-else-if="showComponent === 'watch'"></watch>
  <div v-else>other</div>
</template>

<script>
import { ref } from 'vue'
import ReactiveAndRef from './ReactiveAndRef.vue'
import Watch from './Watch.vue'
export default {
  components: {
    ReactiveAndRef,
    Watch
  },
  setup () {
    const showComponent = ref('reactive&ref')
    function changeComponent (val) {
      console.log(111, val)
      showComponent.value = val
    }
    return {
      showComponent,
      changeComponent
    }
  }
}
</script>

<style scoped>

</style>