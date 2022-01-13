<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <h3>工作种类：{{ person.job.type }}</h3>
  <h3>工作薪水：{{ person.job.salary }}</h3>
  <h3>爱好：{{ person.hobby }}</h3>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import { reactive } from "vue";

export default {
  name: "App",
  setup() {
    //数据
    let person = reactive({
      name: "李四",
      age: 18,
      job: {
        type: "前端",
        salary: "10K",
        a: {
          b: {
            c: 666,
          },
        },
      },
      hobby: ["学习", "看书", "听音乐", "跳舞"],
    });
    function changeInfo() {
      person.age = 50;
      person.name = "张三";
      person.hobby[0] = "打游戏";
      person.job.salary = "30K";
      person.job.a.b.c = 777;
    }
    //返回一个对象（常用）
    return {
      person,
      changeInfo,
    };
  },
};
</script>

<style></style>
