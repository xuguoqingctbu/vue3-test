<template>
  <h3>当前求和为：{{ sum }}</h3>
  <button @click="sum++">SUM的值修改</button>
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
import { reactive, ref, readonly, toRefs } from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    let sum = ref(0);
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    person = readonly(person);
    sum = readonly(sum);
    // person = shallowReadonly(person);
    // sum = shallowReadonly(sum);
    return {
      sum,
      person,
      ...toRefs(person),
    };
  },
};
</script>

<style></style>
