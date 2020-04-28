<template>
  <div @click="add">count.num1: {{ count.num1 }}</div>
  <div>count.num2: {{ count.num2 }}</div>
  <div>count2: {{ count2 }}</div>
  <div>count3: {{ count3 }}</div>
  <div>count4: {{ count4 }}</div>
  <div @click="changeCount6">count6: {{ count6 }}</div>
</template>

<script>
import {reactive, ref, isRef, toRefs, computed, watch} from 'vue'
// import children from "./children";

export default {
  props: {
    ccc: String
  },
  setup(props, context) {
    console.log('props', props, context)
    const state = reactive({
      count: {
        num1: 0,
        num2: computed(() => state.count.num1 * 2)
      }
    })
    const count2 = ref(10)

    const count3 = computed(() => count2.value * 3)
    const count4 = 'noi'
    const count5 = computed(() => state.count.num1 * 5)

    const count6 = computed({
      get: () => count3.value,
      set: val => {
        console.log(456, val)
        count2.value = val
      }
    })

    function add() {
      console.log('add')
      state.count.num1++
      count2.value += 2
    }

    function changeCount6 () {
      count6.value = 123
    }

    console.log(111, isRef(count2), isRef(count3), isRef(state.count.num1), isRef(count5)) // todo 使用computed返回的reactive值ifRef === true
    console.log(222, isRef(count6))

    return {
      add,
      changeCount6,
      count2,
      count3,
      count6,
      count4: 'hello',
      ...toRefs(state)
    }
  }
}
</script>

<style scoped>

</style>