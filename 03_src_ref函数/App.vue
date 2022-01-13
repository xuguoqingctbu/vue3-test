<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ name }}</h2>
  <h2>年龄：{{ age }}</h2>
  <h3>工作种类：{{ job.type }}</h3>
  <h3>工作薪水：{{ job.salary }}</h3>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  setup() {
    //数据
    let name = ref("李四");
    let age = ref(18);
    let job = ref({
      type: "前端",
      salary: "10K",
    });
    function changeInfo() {
      name.value = "张三";
      age.value = 20;
      job.value.type = "JAVA开发工程师";
      job.value.salary = "20K";
    }
    //返回一个对象（常用）
    return {
      name,
      age,
      job,
      changeInfo,
    };
  },
};
</script>

<style></style>
