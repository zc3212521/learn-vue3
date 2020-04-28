<template>
  <h1>Hello Vite + Vue 3!</h1>
<!--  <p>Edit ./App.vue to test hot module replacement (HMR).</p>-->
<!--  <p>-->
<!--    <span>Count is: {{ count }}</span>-->
<!--    <br/>-->
<!--    <span @click="changeName">name is: {{ name }}</span>-->
<!--    <br/>-->
<!--    <button @click="count++">increment</button>-->
<!--  </p>-->
<!--  <com ccc="666"/>-->
  <watch />
</template>

<script>
// import com from './com.vue'
import watch from './watch.vue'
export default {
  components: {
    // com
    watch
  },
  data: () => ({
    count: 0,
    name: 'zhangsan'
  }),
  methods: {
    changeName () {
      this.name = 'lisi'
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
