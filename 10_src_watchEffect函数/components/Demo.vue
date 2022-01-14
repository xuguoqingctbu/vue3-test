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
import { ref, reactive, watchEffect } from "vue";
export default {
  name: "Demo",
  setup() {
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    watchEffect(() => {
      const x1 = msg.value;
      const x2 = person;
      const x3 = person.job.j1.salary;
      console.log("执行了watchEffect函数", x1, x2, x3);
    });
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>

<style></style>
