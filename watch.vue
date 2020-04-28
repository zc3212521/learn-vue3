<template>
  <div>count1: {{ state.count1 }}</div>
  <div>count2: {{ count2 }}</div>
  <button @click="change">change + 1</button>
</template>

<script>
import { reactive, ref, watch} from 'vue'
export default {
  setup () {
    const state = reactive({
      count1: 0
    })
    const count2 = ref(0)

    function change () {
      console.log('change')
      state.count1 += 1
      count2.value += 2
    }
    // 监视单个reactive
    watch(
      () => state.count1,
      (val, preVal) => {
        console.log('watch single reactive', val, preVal)
      }
    )

    // 监视单个ref
    watch(
      count2,
      (val, preVal) => {
        console.log('watch single ref', val, preVal)
      }
    )

    // 监视交叉多个
    watch(
      [() => state.count1, count2],
      ([count1, count2], [preCount1, preCount2]) => {
        console.log('watch mul start')
        console.log('current count1, count2:', count1, count2)
        console.log('pre count1, count2', preCount1, preCount2)
        console.log('watch mul end')
      },
      {
        lazy: true // 在 watch 被创建的时候，不执行回调函数中的代码
      }
    )

    // stop watch
    const stopWachtRef = watch(
      count2,
      (val, preVal) => {
        console.log(' stop watch single ref', val, preVal)
      }
    )
    stopWachtRef()

    // 清除异步任务

    return {
      state,
      count2,
      change
    }
  }
}
</script>

<style scoped>

</style>