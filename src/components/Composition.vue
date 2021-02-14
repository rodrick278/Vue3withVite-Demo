<template>
  <div id="Comp">
    <p>{{ counter }}</p>
    <p>{{ doubleCounter }}</p>
    <p>{{ msg }}</p>
    <p ref="changeData"></p>
  </div>
</template>

<script>
import {
  computed,
  reactive,
  onMounted,
  onUnmounted,
  ref,
  toRefs,
  watch,
} from "vue";

export default {
  name: "Composition",
  setup() { 
    /**
     * counter 相关逻辑
     */
    // 下面写法一样
    // 写法一 reactive：reactive 是用来把引用类型（数组，对象等）做响应式的
    // ============================================
    // const data = reactive({
    //   // data
    //   counter: 1,
    //   // 计算属性
    //   doubleCounter: computed(() => data.counter * 2),
    // });
    // // 转换成ref值,ref的值要用xx.value调用
    // let { counter, doubleCounter } = toRefs(data);
    // ===========================================

    // 写法二 ref：是把值类型做响应式的
    // ===========================================
    let counter = ref(1);
    let doubleCounter = computed(() => counter.value * 2);
    // ===========================================

    let timer;
    // 生命周期，加上onXXX destroyed -> onUnmounted
    onMounted(() => {
      timer = setInterval(() => {
        // console.log("onMounted", data.counter);
        counter.value++;
      }, 1000);
    });

    onUnmounted(() => {
      // alert("onUnmounted");
      clearInterval(timer);
    });

    /**
     * 其他数据逻辑
     */
    const msg = ref("some msg");

    // dom ref
    const changeData = ref(null);

    // 监听【注意第一个参数如果是ref的话直接写，否则的话要写成()=>xx.count】
    watch(counter, (now, old) => {
      // changeData.value 获得的就是这个 ref dom
      changeData.value.textContent = `counter changed from ${old} to ${now}`;
    });

    /**
     * 最后返回给setup之外用的
     */
    return { msg, counter, doubleCounter, changeData };
  },
};

// function useCounter() {
//   const data = reactive({
//     // data
//     counter: 1,
//     // 计算属性
//     doubleCounter: computed(() => data.counter * 2),
//   });

//   let timer;
//   // 生命周期，加上onXXX destroyed -> onUnmounted
//   onMounted(() => {
//     timer = setInterval(() => {
//       // console.log("onMounted", data.counter);
//       data.counter++;
//     }, 1000);
//   });

//   onUnmounted(() => {
//     // alert("onUnmounted");
//     clearInterval(timer);
//   });
//   // toRefs 会把响应式的 data 里的每个值都变成单值ref对象，这样外面用的时候就可以解构取值
//   return toRefs(data);
// }
</script>

<style scoped>
</style>