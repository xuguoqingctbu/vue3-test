<template>
  <h1>一个人的信息</h1>
  <h2>当前SUM的值为：{{ sum }}</h2>
  <button @click="sum++">点击SUM加1</button>
  <hr />
  <h2>当前信息为：{{ msg }}</h2>
  <button @click="msg += '!'">修改msg</button>
  <hr />
  <h3>当前此人的名字为：{{ person.name }}</h3>
  <h3>当前此人的年龄为：{{ person.age }}</h3>
  <h3>当前此人的薪水为：{{ person.job.j1.salary }}</h3>
  <button @click="person.name += '~'">修改姓名</button>
  <button @click="person.age++">增长年龄</button>
  <button @click="person.job.j1.salary++">涨薪</button>
</template>

<script>
import { ref } from "@vue/reactivity";
import { watch } from "@vue/runtime-core";
export default {
  name: "Demo",
  setup() {
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = ref({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    //情况一：监视ref所定义的一个响应式数据
    watch(
      sum,
      (newValue, oldValue) => {
        console.log(`sum的值变化了,新值为:${newValue},旧值为：${oldValue}`);
      },
      { immediate: true }
    );
    // 监视ref 发现也无法得到旧值，因为ref,也会求助与reactive，
    // 但是监视ref对象，需要开启深度监视才会起监视作用，不然不会监视
    watch(
      person,
      (newValue, oldValue) => {
        console.log("person的值被修改了！！", newValue, oldValue);
      },
      { deep: true }
    );
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>

<style></style>
