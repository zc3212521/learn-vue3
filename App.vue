<template>
  <h1>Hello Vite + Vue 3!</h1>
  <div>message is {{ msg1 }} {{msg2}}</div>
  <br />
  <children />
</template>

<script>
import { reactive } from 'vue'
import Children from './components/Children.vue'
export default {
  components: {
    Children
  },
  data: () => ({
    msg1: 'hello'
  }),
  setup () {
    const msg2 = 'world'
    return {
      msg2
    }
  }
}
</script>

<style scoped>
h1 {
  color: #4fc08d;
}

h1, p {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
