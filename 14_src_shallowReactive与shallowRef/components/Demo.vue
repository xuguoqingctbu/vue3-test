<template>
  <h3>当前x.y的值为{{ x.y }}</h3>
  <button @click="x.y++">x.y的值++</button>
  <button @click="x = { y: 1 }">替换x</button>
  <hr />
  <h1>一个人的信息</h1>
  <h2>person:{{ person }}</h2>
  <h3>当前此人的名字为：{{ name }}</h3>
  <h3>当前此人的年龄为：{{ age }}</h3>
  <h3>当前此人的薪水为：{{ job.j1.salary }}</h3>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
</template>

<script>
import { reactive, shallowRef, toRef, toRefs } from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    // let person = shallowReactive({
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    let x = shallowRef({
      y: 0,
    });
    const x1 = toRef(person, "job");
    console.log(x1);
    return {
      x,
      person,
      ...toRefs(person),
    };
  },
};
</script>

<style></style>
